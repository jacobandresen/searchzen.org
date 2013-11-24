---
layout: post
title: "Brug af java reflection til at generere JSON data"
date: 2009-02-08 10:02
comments: true 
categories: 
---
Jeg arbejder iøjeblikket på en opgave , hvor jeg har behov for at bringe datamodellen ud til behandling i javascript på en nem facon . Ifbm med denne opgave har jeg tænkt på hvordan man kunne gøre det vha reflection.

Hvis vi antager flg klasser :

<code lang="java">
class A{
  public int B;
  public int C;
  public D F;
  public D G;
};

class D {
  public String E;
}
</code>

og at de var initialiseret således:
<code lang="java">
A a=new A();
a.B=1;
a.C=2;
a.F=new D();
a.F.E="test";
a.G=new D();
a.G.E="test2";
</code>

Så kunne man kigge på selve java objekterne vha reflection for at generere JSON output til bruge i javascript således:

<code lang="java">
public class JsonEmit{
  public static String emit(Object target) throws Exception{
     StringBuilder sb=new StringBuilder();
     sb.append("{");
     Class targetClass=target.getClass();
     Field[] publicFields = targetClass.getFields();
     for (int i=0;i<publicFields.length;i++){
       String sFieldName = publicFields[i].getName();
       Class typeClass = publicFields[i].getType();
       String sFieldType = typeClass.getName();
       Object value = publicFields[i].get(target);
       if(value!=null){
         sb.append(sFieldName+":");
         if(typeClass.isPrimitive()
         ||sFieldType=="java.lang.String"){
         sb.append("""+value.toString()+""");
      }else{
        sb.append(JsonEmit.emit(value));
      }
    }
    if(i!=(publicFields.length-1))
      sb.append(",");
  }
 sb.append("}");
 return(sb.toString());
}
</code>

På den facon vil man kunne genere JSON ved et simpelt kald til
<code lang="java">
JsonEmit.emit(a)
</code>

hvorefter man vil se
<code lang="javascript">
{B:"1",C:"2",F:{E:"test"},G:{E:"test2"}}
</code>