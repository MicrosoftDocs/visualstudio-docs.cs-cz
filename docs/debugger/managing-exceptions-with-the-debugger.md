---
title: Správa výjimek pomocí ladicího programu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 10/09/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02c7fbfca9a63ac736972ebea01a854e24f90188
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057915"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Správa výjimek pomocí ladicího programu v sadě Visual Studio

Výjimkou je údaj o chybovém stavu, ke které dojde při spuštění programu. Ladicí program můžete zjistit, jaké výjimky nebo sady výjimky na přerušení na a kdy chcete, aby ladicí program na přerušení. Pokud ladicí program přeruší, to se dozvíte, kde byla výjimka vydána. Můžete také přidat nebo odstranit výjimky. Pomocí řešení otevřít v sadě Visual Studio, **ladit > Windows > Nastavení výjimek** otevřít **nastavení výjimek** okna.

Poskytuje rutiny, které reagují na nejdůležitější výjimky. Naučte se konfigurovat ladicí program přeruší běh o některých výjimkách, vždy.

Když dojde k výjimce, ladicí program zapíše zprávu o výjimce do **výstup** okna. To může přerušit provádění, v následujících případech, kdy:

- Je vyvolána výjimka, která není zpracována.
- Ladicí program je nakonfigurován na přerušit provádění, před vyvoláním libovolné obslužné rutiny.
- Jste nastavili [pouze můj kód](../debugger/just-my-code.md), a ladicí program je nakonfigurován na přerušení na jakékoli výjimce, která není ošetřena v uživatelském kódu.

> [!NOTE]
> Technologie ASP.NET obsahuje obslužnou rutinu výjimky nejvyšší úrovně, která se zobrazí chybové stránky v prohlížeči. Nelze přerušit provádění, není-li **pouze můj kód** zapnutý. Příklad najdete v tématu [řekněte ladicího programu, pokračujte na uživatelem neošetřené výjimky](#BKMK_UserUnhandled) níže.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> V aplikaci Visual Basic ladicí program spravuje všechny chyby jako výjimky, i v případě, že se používá ve stylu obslužné rutiny chyb.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Řekněte ladicí program na přerušení při vyvolání výjimky

Ladicí program může přerušit provádění v místě, kde je vyvolána výjimka, tak může zkoumat výjimky, předtím, než je vyvolána obslužná rutina.

V **nastavení výjimek** okno (**ladit > Windows > Nastavení výjimek**), rozbalte uzel pro kategorii výjimek, jako například **výjimky modulu Common Language Runtime**. Zaškrtněte políčko pro určité výjimky v rámci dané kategorie, jako například **System.AccessViolationException**. Můžete také vybrat celou kategorii výjimek.

![Checked výjimka AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Specifické výjimky můžete najít pomocí **hledání** okna v **nastavení výjimek** nástrojů nebo pomocí vyhledávání filtrujte pro konkrétní obory názvů (například **System.IO**).

Pokud vyberete výjimku v **nastavení výjimek** okně spuštění ladicího programu se přeruší, bez ohledu na to je vyvolána výjimka bez ohledu na to, zda je zpracována. Výjimka je teď jmenuje první odpovídající výjimce. Například tady je několik scénářů:

- V následující konzoly aplikace v C#, vyvolá metoda Main **výjimka AccessViolationException** uvnitř `try/catch` bloku.

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

  Pokud máte **výjimka AccessViolationException** změnami **nastavení výjimek**, spuštění se přeruší na `throw` řádku při spuštění tohoto kódu v ladicím programu. Potom můžete pokračovat v provádění. Konzole by měl zobrazit obě čáry:

  ```cmd
  caught exception
  goodbye
  ```

  ale nejsou zobrazeny `here` řádku.

- Konzolová aplikace jazyka C# odkazuje na knihovnu tříd s třídou, která má dvě metody. Jedna metoda vyvolá výjimku a to všechno zvládne, zatímco druhá metoda vyvolá výjimku stejné, ale nemůže pracovat.

  ```csharp
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

  Pokud máte **výjimka AccessViolationException** změnami **nastavení výjimek**, spuštění se přeruší na `throw` řádku v obou **ThrowHandledException()** a **ThrowUnhandledException()** při spuštění tohoto kódu v ladicím programu.

Chcete-li obnovit výchozí hodnoty nastavení výjimek, zvolte **obnovit seznam do výchozího nastavení** tlačítka:

![Obnovit výchozí nastavení v nastavení výjimek](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>Informace ladicího programu, pokračujte na výjimkách neošetřených uživatelem

Pokud ladíte kód .NET nebo JavaScript s [pouze můj kód](../debugger/just-my-code.md), poznáte, ladicí program, aby se zabránilo přerušení při výjimkách, které nejsou zpracovány v uživatelském kódu, ale jsou zpracovány jinde.

1. V **nastavení výjimek** okno, otevřete místní nabídku kliknutím pravým tlačítkem myši popisky sloupců a pak vyberte **zobrazit sloupce > Další akce**. (Pokud jste vypnuli **pouze můj kód**, tento příkaz nezobrazí.) Třetí sloupec s názvem **další akce** se zobrazí.

   ![Další sloupec akce](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Pro výjimku, která ukazuje **pokračovat, pokud není ošetřená v uživatelském kódu** v tomto sloupci, ladicí program pokračuje, pokud tato výjimka není ošetřena v uživatelském kódu, ale se řeší externě.

2. Chcete-li změnit toto nastavení pro konkrétní výjimky, vyberte výjimky, klikněte pravým tlačítkem myši zobrazit místní nabídku a vyberte **pokračovat po neošetřené v uživatelském kódu**. Můžete také změnit nastavení pro celou kategorii výjimek, jako je například celý výjimky Common Language Runtime).

   ![** Pokračovat, pokud není ošetřená v nastavení uživatelského kódu **](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Například webové aplikace ASP.NET zpracování výjimek převedením na stavový kód HTTP 500 ([zpracování výjimek v rozhraní ASP.NET Web API](http://www.asp.net/web-api/overview/error-handling/exception-handling)), které možná vám pomůže určit zdroj výjimky. V následujícím příkladu kód uživatele provede volání `String.Format()` , které vyvolá <xref:System.FormatException>. Provádění přeruší následujícím způsobem:

![Dojde k porušení uživatele&#45;neošetřená výjimka](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Přidávání a odstraňování výjimek

Můžete přidat a odstranit výjimky. Pokud chcete odstranit typ výjimky z kategorie, vyberte výjimku a zvolte **odstraní vybranou výjimku ze seznamu** na tlačítko (znaménko minus) **nastavení výjimek** nástrojů. Případně může klikněte pravým tlačítkem na výjimku a vybrat **odstranit** z místní nabídky. Odstraňuje se výjimka má stejný účinek jako s výjimkou není zaškrtnuto, což je, že ladicí program nebude přerušit, pokud je vyvolána výjimka.

Chcete-li přidat výjimku:

1. V **nastavení výjimek** okna, vyberte jednu z výjimek kategorií (například **Common Language Runtime**).

2. Zvolte **přidat výjimku do vybrané kategorie** tlačítko (znaménko plus).

   ![** Přidat výjimku do vybrané kategorie ** tlačítko](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Zadejte název výjimky (například **System.UriTemplateMatchException**).

   ![Zadejte název výjimky](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Výjimka je přidán do seznamu (v abecedním pořadí) a automaticky zaškrtnuto.

Pokud chcete přidat výjimku do výjimky přístupu k paměti GPU, zahrnují výjimky modulu Runtime jazyka JavaScript nebo kategorie výjimky Win32, kód chyby a popis.

> [!TIP]
> Zkontrolujte pravopis! **Nastavení výjimek** okna nebude kontrolovat přítomnost přidané výjimky. Pokud zadáte **Sytem.UriTemplateMatchException**, zobrazí se položka pro tuto výjimku (a ne pro **System.UriTemplateMatchException**).

Nastavení výjimek jsou zachované v soubor .suo řešení, takže se vztahují na konkrétní řešení. Nastavení konkrétní výjimky nelze opětovně použít napříč řešeními. Nyní jsou trvalé pouze přidaných výjimek; odstraněné výjimky nejsou. Můžete přidat výjimku, zavřete a znovu otevřete řešení a výjimka bude stále existovat. Ale pokud odstraníte výjimku a zavřete a znova otevřete řešení, se znovu zobrazí výjimka.

**Nastavení výjimek** okna podporuje výjimek obecného typu v jazyce C#, ale ne v jazyce Visual Basic. Na přerušení na jako `MyNamespace.GenericException<T>`, je nutné přidat výjimku jako **MyNamespace.GenericException'1**. To znamená pokud jste vytvořili výjimku přibližně takto:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Můžete přidat výjimku **nastavení výjimek** pomocí předchozího postupu:

![Přidání obecné výjimky](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Přidání podmínky do výjimky

Použití **nastavení výjimek** okno Nastavení podmínek v výjimky. Aktuálně se podporují příkladem podmínek může být její název modulu pro zahrnutí nebo vyloučení pro výjimku. Nastavením názvů modulů jako podmínky můžete přerušit pro výjimku pouze na určité moduly kódu. Také můžete vyhnout rozdělení na konkrétní moduly.

> [!NOTE]
> Přidání podmínky do výjimky je novinkou systémů [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Přidat podmíněné výjimky:

1. Zvolte **upravit podmínky** tlačítko v okně Nastavení výjimek nebo klikněte pravým tlačítkem na výjimku a zvolte **upravit podmínky**.

   ![Podmínky pro výjimku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Chcete-li přidat další požadované podmínky na výjimku, **přidat podmínku** pro každou novou podmínku. Další podmínky řádky se zobrazí.

   ![Dodatečné podmínky pro výjimku](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Pro každý řádek podmínku, zadejte název modulu a změny seznamu operátor porovnání k **rovná** nebo **nerovná**. Můžete zadat zástupné znaky (**\\***) v názvu k určení více než jeden modul.

4. Pokud je potřeba odstranit podmínky, zvolte **X** na konci řádku podmínku.

## <a name="see-also"></a>Viz také:

[Pokračování ve spuštění po výjimce](../debugger/continuing-execution-after-an-exception.md)<br/>
[Postupy: Kontrola systémového kódu po výjimce](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
[Postupy: Použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)<br/>
[Použití kontrol za běhu bez běhové knihovny jazyka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
[Kurz: Zjistěte, jak ladit pomocí sady Visual Studio](../debugger/getting-started-with-the-debugger.md)
