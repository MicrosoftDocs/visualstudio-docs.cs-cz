---
title: Správa výjimek pomocí ladicího programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 5303a8003d84af5e2a059d9f509e560204afa528
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301090"
---
# <a name="managing-exceptions-with-the-debugger"></a>Správa výjimek pomocí ladicího programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Výjimkou je údaj o chybovém stavu, ke které dojde při spuštění programu. Můžete a byste měli poskytnout obslužné rutiny, které reagují na nejdůležitější výjimky, ale je důležité znát, jak nastavit ladicí program pro přerušení pro výjimky, které chcete zobrazit.  
  
 Pokud dojde k výjimce, ladicí program zapíše zprávu o výjimce do okna výstup. Může dojít k přerušení provádění v následujících případech:  
  
- Když je vyvolána výjimka a není zpracována.  
  
- Když je ladicí program nastaven na přerušení provádění okamžitě při vyvolání výjimky, před vyvoláním jakékoli obslužné rutiny.  
  
- Pokud jste nastavili [pouze můj kód](../debugger/just-my-code.md)a ladicí program je nastaven na přerušení na jakékoli výjimce, která není zpracována v uživatelském kódu.  
  
> [!NOTE]
> Technologie ASP.NET obsahuje obslužnou rutinu výjimky nejvyšší úrovně, která se zobrazí chybové stránky v prohlížeči. Neprovádí přerušit provádění, pokud není zapnuto **pouze můj kód** . Příklad naleznete v tématu [nastavení ladicího programu pro pokračování v neošetřených výjimkách uvedených uživatelem](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) .  
  
> [!NOTE]
> V Visual Basic aplikaci spravuje ladicí program všechny chyby jako výjimky, a to i v případě, že použijete rutiny chyb typu Error-Style.  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>Správa výjimek pomocí okna Nastavení výjimek  
 Pomocí okna **nastavení výjimky** můžete určit, které výjimky (nebo sady výjimek) způsobí přerušení ladicího programu a v jakém místě chcete přerušit. Můžete přidat nebo odstranit výjimky nebo zadat výjimky pro přerušení. Otevřete toto okno, když je otevřeno řešení, kliknutím na **ladit/Windows/nastavení výjimky**.  
  
 Konkrétní výjimky můžete najít pomocí okna **hledání** na panelu nástrojů **Nastavení výjimek** nebo pomocí hledání filtrovat konkrétní obory názvů (například **System.IO**).  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>Nastavení ladicího programu pro přerušení při vyvolání výjimky  
 Ladicí program může přerušit provádění v místě, kde je vyvolána výjimka, což vám dává možnost před vyvoláním obslužné rutiny ověřit výjimku.  
  
 V okně **Nastavení výjimek** rozbalte uzel pro kategorii výjimek (například **výjimky modulu CLR (Common Language Runtime**), tzn. výjimky rozhraní .NET) a zaškrtněte políčko pro konkrétní výjimku v této kategorii (například **System. AccessViolationException –** ). Můžete také vybrat celou kategorii výjimek.  
  
 ![Zaškrtnuté AccessViolationException –](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 Pokud zaškrtnete danou výjimku, spuštění ladicího programu bude přerušeno všude, kde je vyvolána výjimka, bez ohledu na to, zda je zpracována nebo neošetřena. V tomto okamžiku je výjimka označována jako výjimka první pravděpodobnost. Například tady je několik scénářů:  
  
1. V následující C# konzolové aplikaci vyvolá metoda Main **accessviolationexception –** uvnitř bloku `try/catch`:  
  
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
  
    Pokud jste **AccessViolationException –** **Nastavení výjimek**, při spuštění tohoto kódu v ladicím programu dojde k přerušení na `throw`ovém řádku. Potom můžete pokračovat v provádění. Konzole by měl zobrazit obě čáry:  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    ale nezobrazuje `here` řádek.  
  
2. C# Konzolová aplikace odkazuje na knihovnu tříd se třídou, která má dvě metody, metodu, která vyvolá výjimku a zpracovává ji a druhou metodu, která vyvolá stejnou výjimku a nezpracovává ji:  
  
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
  
    Zde je metoda Main () konzolové aplikace:  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       Class1 class1 = new Class1();  
       class1.ThrowHandledException();  
       class1.ThrowUnhandledException();  
   }  
   ```  
  
    Pokud jste **AccessViolationException –** **Nastavení výjimek**, při spuštění tohoto kódu v ladicím programu dojde k přerušení na `throw`ovém řádku v **ThrowHandledException ()** a **ThrowUnhandledException ()** .  
  
   Pokud chcete obnovit výchozí nastavení výjimek, můžete kliknout na tlačítko **obnovit** na panelu nástrojů:  
  
   ![Obnovit výchozí hodnoty v nastavení výjimky](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
### <a name="BKMK_UserUnhandled"></a>Nastavení ladicího programu pro pokračování v neošetřených výjimkách uživatele  
 Pokud ladíte kód .NET nebo JavaScript pomocí [pouze můj kód](../debugger/just-my-code.md), můžete určit, že ladicí program nebude přerušovat na výjimkách, které nejsou zpracovány v uživatelském kódu, ale jsou zpracovávány někde jinde.  
  
1. V okně **nastavení výjimky** otevřete kontextovou nabídku tak, že kliknete pravým tlačítkem v okně a pak vyberete **Zobrazit sloupce**. (Pokud jste vypnuli **pouze můj kód**, tento příkaz se nezobrazí.)  
  
2. Měl by se zobrazit druhý sloupec s názvem **Další akce**. V tomto sloupci se zobrazí **pokračování, pokud je neošetřeno uživatelským kódem** na konkrétní výjimky, což znamená, že ladicí program není přerušen, pokud tato výjimka není zpracována v uživatelském kódu, ale je zpracována v externím kódu.  
  
3. Toto nastavení můžete změnit buď pro konkrétní výjimku (vyberte výjimku, kliknete pravým tlačítkem myši a vyberete/zrušíte výběr **pokračovat, pokud je neošetřeno v uživatelském kódu**), nebo pro celou kategorii výjimek (například všechny výjimky modulu CLR (Common Language Runtime)).  
  
   Například webové aplikace ASP.NET zpracovávají výjimky jejich převodem na stavový kód HTTP 500 ([zpracování výjimek v rozhraní ASP.NET API](https://docs.microsoft.com/aspnet/web-api/overview/error-handling/exception-handling)), které vám nemusí pomáhat určit zdroj výjimky. V následujícím příkladu kód uživatele provede volání `String.Format()`, které vyvolá <xref:System.FormatException>. Provádění přeruší následujícím způsobem:  
  
   ![unhanlded výjimky na&#45;uživateli](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>Přidávání a odstraňování výjimek  
 Můžete přidat a odstranit výjimky. Libovolný typ výjimky z libovolné kategorie můžete odstranit tak, že vyberete výjimku a na panelu nástrojů **Nastavení výjimek** kliknete na tlačítko **Odstranit** (symbol mínus), nebo kliknete pravým tlačítkem na výjimku a vyberete **Odstranit** z kontextové nabídky. Odstranění výjimky má stejný účinek jako u nezaškrtnuté výjimky, což znamená, že ladicí program nebude při vyjímka přerušen.  
  
 Chcete-li přidat výjimku: v okně **nastavení výjimky** vyberte jednu z kategorií výjimek (například **modul CLR (Common Language Runtime**) a klikněte na tlačítko **Přidat** . Zadejte název výjimky (například. **System. UriTemplateMatchException**). Výjimka se přidá do seznamu (v abecedním pořadí) a automaticky se zaškrtne.  
  
 Chcete-li přidat výjimku do výjimek přístupu k paměti GPU, výjimek modulu runtime jazyka JavaScript nebo kategorií výjimek Win32, je nutné zahrnout kód chyby a také popis.  
  
> [!TIP]
> Zkontrolujte pravopis! Okno **nastavení výjimky** nekontroluje existenci přidané výjimky. Takže pokud zadáte **Sytem. UriTemplateMatchException**, dostanete položku pro tuto výjimku (a ne pro **System. UriTemplateMatchException**).  
  
 Nastavení výjimek jsou trvalá v souboru. suo řešení, takže se vztahují na konkrétní řešení. V rámci řešení nemůžete znovu použít specifická nastavení výjimek. V tomto okamžiku jsou trvalé pouze přidané výjimky; odstraněné výjimky nejsou. Jinými slovy, můžete přidat výjimku, zavřít a znovu otevřít řešení a výjimka bude i nadále. Ale pokud odstraníte výjimku a zavřete a znova otevřete řešení, se znovu zobrazí výjimka.  
  
 Okno **nastavení výjimky** podporuje typy obecných výjimek v, C# ale ne v Visual Basic. Pro přerušení na výjimkách, jako je `MyNamespace.GenericException<T>`, je nutné přidat výjimku jako **MyNamespace. GenericException ' 1**. To znamená, že pokud jste vytvořili výjimku, například:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Výjimku můžete přidat do **nastavení výjimky** , například takto:  
  
 ![přidává se obecná výjimka.](../debugger/media/addgenericexception.png "AddGenericException")  
  
## <a name="see-also"></a>Viz také  
 [Pokračování v provádění po  výjimky](../debugger/continuing-execution-after-an-exception.md)  
 [Postupy: Kontrola systémového kódu po výjimce](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Postupy: použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)   
 [Použití kontrol za běhu bez běhové knihovny jazyka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Pomocník pro výjimky](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)   
 [Základy ladicího programu](../debugger/debugger-basics.md)
