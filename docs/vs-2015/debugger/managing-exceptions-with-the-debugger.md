---
title: Správa výjimek pomocí ladicího programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdb648e7a29b3ed5d9a444e203ddbdcd6b0e73dc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769998"
---
# <a name="managing-exceptions-with-the-debugger"></a>Správa výjimek pomocí ladicího programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Výjimkou je údaj o chybovém stavu, ke které dojde při spuštění programu. Můžete a měl by poskytovat obslužné rutiny, které reagují na nejdůležitější výjimky, ale je důležité vědět, jak nastavit ladicí program na přerušení pro výjimky, které chcete zobrazit.  
  
 Když dojde k výjimce, ladicí program zapíše zprávu o výjimce do okna výstup. To může přerušit provádění, v následujících případech:  
  
-   Výjimku při vyvolání a není zpracována.  
  
-   Pokud ladicí program nastavená na přerušit běh, okamžitě, když je vyvolána výjimka, před vyvoláním libovolné obslužné rutiny.  
  
-   Pokud jste nastavili [pouze můj kód](../debugger/just-my-code.md), a ladicí program na přerušení na jakékoli výjimce, která není ošetřena v uživatelském kódu.  
  
> [!NOTE]
>  Technologie ASP.NET obsahuje obslužnou rutinu výjimky nejvyšší úrovně, která se zobrazí chybové stránky v prohlížeči. To není přerušit provádění, není-li **pouze můj kód** zapnutý. Příklad najdete v tématu [nastavení ladicího programu, pokračujte na uživatelem neošetřené výjimky](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) níže.  
  
> [!NOTE]
>  V aplikaci Visual Basic ladicí program spravuje všechny chyby jako výjimky, i v případě, že se používá ve stylu chyba obslužné rutiny chyb.  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>Správa výjimek pomocí okna Nastavení výjimek  
 Můžete použít **nastavení výjimek** okně zadejte výjimky (nebo sadu výjimek) způsobí přerušení ladicího programu a kdy se má přerušit. Můžete přidat nebo odstranit výjimky nebo výjimky na přerušení na zadat. Při řešení otevřené kliknutím otevřete toto okno **ladění / Windows / nastavení výjimek**.  
  
 Specifické výjimky můžete najít pomocí **hledání** okna **nastavení výjimek** nástrojů nebo pomocí vyhledávání filtrujte pro konkrétní obory názvů (například **System.IO**).  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>Nastavení ladicí program na přerušení při vyvolání výjimky  
 Ladicí program může přerušit provádění v místě, kde je vyvolána výjimka, s možností prověřit výjimky před vyvoláním obslužné rutiny.  
  
 V **nastavení výjimek** okna, rozbalte uzel pro kategorii výjimek (například **výjimky modulu Common Language Runtime**, což znamená výjimky .NET) a zaškrtněte políčko pro konkrétní výjimky v rámci dané kategorie (například **System.AccessViolationException**). Můžete také vybrat celou kategorii výjimek.  
  
 ![Checked výjimka AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 Pokud zaškrtnete danou výjimku, přeruší běh ladicího programu bez ohledu na to je vyvolána výjimka bez ohledu na to, zda je zpracovat nebo neošetřená. Výjimky v tomto okamžiku se nazývá první odpovídající výjimce. Například tady je několik scénářů:  
  
1. V následující konzoly aplikace v C#, vyvolá metoda Main **výjimka AccessViolationException** uvnitř `try/catch` blok:  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       try  
       {  
           throw new AccessViolationException();  
           Console.WriteLine("here");  
       }  
       catch (Exception e)  
       {  
           Console.WriteLine("caught exception");  
       }  
       Console.WriteLine("goodbye");  
   }  
   ```  
  
    Pokud máte **výjimka AccessViolationException** změnami **nastavení výjimek**, při spuštění tohoto kódu při provádění ladicí program přeruší na `throw` řádku. Potom můžete pokračovat v provádění. Konzole by měl zobrazit obě čáry:  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    Tady nezobrazují, ale `here` řádku.  
  
2. Konzolová aplikace jazyka C# odkazuje na knihovnu tříd s třídou, která má dvě metody, metoda, která vyvolá výjimku a to všechno zvládne a druhá metoda, která vyvolá stejnou výjimku a nelze ji zpracovat:  
  
   ```vb  
   public class Class1  
   {  
       public void ThrowHandledException()  
       {  
           try  
           {  
               throw new AccessViolationException();  
           }  
           catch (AccessViolationException ave)  
           {  
               Console.WriteLine("caught exception" + ave.Message);  
           }  
       }  
  
       public void ThrowUnhandledException()  
       {  
           throw new AccessViolationException();  
       }  
   }  
   ```  
  
    Tady je metoda Main() konzolové aplikace:  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       Class1 class1 = new Class1();  
       class1.ThrowHandledException();  
       class1.ThrowUnhandledException();  
   }  
   ```  
  
    Pokud máte **výjimka AccessViolationException** změnami **nastavení výjimek**, při spuštění tohoto kódu při provádění ladicí program přeruší na `throw` řádku v obou  **ThrowHandledException()** a **ThrowUnhandledException()**.  
  
   Pokud chcete obnovit výchozí hodnoty nastavení výjimek, můžete kliknout **obnovení** tlačítko na panelu nástrojů:  
  
   ![Obnovit výchozí nastavení v nastavení výjimek](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
###  <a name="BKMK_UserUnhandled"></a> Nastavení ladicího programu, pokračujte na výjimkách neošetřených uživatelem  
 Pokud ladíte kód .NET nebo JavaScript s [pouze můj kód](../debugger/just-my-code.md), můžete říct, aby ladicí program není pozastavte běh při výjimkách, které nejsou zpracovány v uživatelském kódu, ale jsou zpracovány někde jinde.  
  
1. V **nastavení výjimek** okno, otevřete místní nabídku v okně pravým tlačítkem a výběrem **zobrazit sloupce**. (Pokud jste nevypnuli **pouze můj kód**, tento příkaz nezobrazí.)  
  
2. Měli byste vidět druhý sloupec s názvem **další akce**. Tento sloupec zobrazuje **pokračovat, pokud není ošetřená v uživatelském kódu** na konkrétní výjimky, což znamená, že ladicí program není přerušit, pokud tato výjimka není ošetřena v uživatelském kódu, ale je zpracována v externí kód.  
  
3. Můžete změnit toto nastavení, buď pro konkrétní výjimce (Vyberte výjimky, klikněte pravým tlačítkem a vyberte nebo zrušte zaškrtnutí možnosti **pokračovat, pokud není ošetřená v uživatelském kódu**) nebo pro celou kategorii výjimek (například všechny společné Výjimky modulu CLR).  
  
   Například webové aplikace ASP.NET zpracování výjimek převedením na stavový kód HTTP 500 ([zpracování výjimek v rozhraní API pro ASP.NET](http://www.asp.net/web-api/overview/error-handling/exception-handling)), které možná vám pomůže určit zdroj výjimky. V následujícím příkladu kód uživatele provede volání `String.Format()` , které vyvolá <xref:System.FormatException>. Provádění přeruší následujícím způsobem:  
  
   ![dojde k porušení uživatele&#45;unhanlded výjimka](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>Přidávání a odstraňování výjimek  
 Můžete přidat a odstranit výjimky. Odstraněním jakéhokoli typu výjimky z libovolné kategorie výběrem výjimku a kliknutím na **odstranit** na tlačítko (znaménko minus) **nastavení výjimek** nástrojů nebo pravým tlačítkem myši na výjimku a Výběr **odstranit** v místní nabídce. Odstraňuje se výjimka má stejný účinek jako s výjimkou není zaškrtnuto, což je, že ladicí program nebude přerušit, pokud je vyvolána výjimka.  
  
 Přidat výjimku: v **nastavení výjimek** okna, vyberte jednu z výjimek kategorií (například **Common Language Runtime**) a klikněte na tlačítko **přidat** tlačítko. Zadejte název výjimky (například. **System.UriTemplateMatchException**). Výjimka je přidán do seznamu (v abecedním pořadí) a je automaticky zaškrtnuto.  
  
 Pokud chcete přidat výjimku výjimky přístupu k paměti GPU, výjimky modulu Runtime jazyka JavaScript nebo kategorií výjimky Win32, budete muset zahrnout kód chyby, stejně jako popis.  
  
> [!TIP]
>  Zkontrolujte pravopis! **Nastavení výjimek** okna nebude kontrolovat přítomnost přidané výjimky. Pokud zadáte **Sytem.UriTemplateMatchException**, zobrazí se položka pro tuto výjimku (a ne pro **System.UriTemplateMatchException**).  
  
 Nastavení výjimek jsou zachované v soubor .suo řešení, takže se vztahují na konkrétní řešení. Nastavení konkrétní výjimky nelze opětovně použít napříč řešeními. V tomto okamžiku jsou trvalé pouze přidaných výjimek; odstraněné výjimky nejsou. Jinými slovy můžete přidat výjimku, zavřete a znovu otevřete řešení a výjimka bude stále existovat. Ale pokud odstraníte výjimku a zavřete a znova otevřete řešení, se znovu zobrazí výjimka.  
  
 **Nastavení výjimek** okna podporuje výjimek obecného typu v jazyce C#, ale ne v jazyce Visual Basic. Na přerušení na jako `MyNamespace.GenericException<T>`, je nutné přidat výjimku jako **MyNamespace.GenericException'1**. To znamená pokud jste vytvořili výjimku takto:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Můžete přidat výjimku **nastavení výjimek** tímto způsobem:  
  
 ![Přidání obecné výjimky](../debugger/media/addgenericexception.png "AddGenericException")  
  
## <a name="see-also"></a>Viz také  
 [Pokračování v provádění po výjimce](../debugger/continuing-execution-after-an-exception.md)   
 [Postupy: Kontrola systémového kódu po výjimce](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Postupy: použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)   
 [Pomocí za běhu bez běhové knihovny jazyka C kontrol](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Pomocníka pro výjimky](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)   
 [Základy ladicího programu](../debugger/debugger-basics.md)





