---
title: Správa výjimek pomocí ladicího | Microsoft Docs
description: Zjistěte, jak určit výjimky, na kterých se ladicí program přeruší, kdy chcete ladicí program přerušit a jak se zpracovávají přerušení.
ms.custom: SEO-VS-2020
ms.date: 10/09/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89795df3a4c6b87c6a878cd07a072027f880e660
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390421"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Správa výjimek pomocí ladicího programu v Visual Studio

Výjimka je indikací chybového stavu, ke kterému dochází při spuštění programu. Ladicímu programu můžete říct, na které výjimky nebo sady výjimek se mají přerušit, a v kterém okamžiku chcete ladicí program přerušit (to znamená pozastavit v ladicím programu). Když se ladicí program přeruší, zobrazí se místo vyvolání výjimky. Můžete také přidat nebo odstranit výjimky. Když máte řešení otevřené v Visual Studio, otevřete okno Nastavení výjimek pomocí > **nastavení > windows >** výjimek. 

Poskytují obslužné rutiny, které reagují na nejdůležitější výjimky. Pokud potřebujete vědět, jak přidat obslužné rutiny pro výjimky, najdete informace v tématu Oprava [chyb psaním lepšího kódu jazyka C#.](../debugger/write-better-code-with-visual-studio.md) Zjistěte také, jak nakonfigurovat ladicí program tak, aby u některých výjimek vždy přerušil provádění.

Když dojde k výjimce, ladicí program zapíše zprávu o výjimce do **okna** Výstup. Provádění může přerušit v následujících případech, kdy:

- Je vyvolána výjimka, která není zpracována.
- Ladicí program je nakonfigurován tak, aby před vyvoláním jakékoli obslužné rutiny přerušil provádění.
- Nastavili jste [Pouze můj kód](../debugger/just-my-code.md)a ladicí program je nakonfigurovaný tak, aby přerušil jakoukoli výjimku, která není zpracována v uživatelském kódu.

> [!NOTE]
> ASP.NET má obslužnou rutinu výjimek nejvyšší úrovně, která v prohlížeči zobrazuje chybové stránky. Provádění se nenaruší, pokud **Pouze můj kód** zapnutý. Příklad naleznete v části Tell [the debugger to continue on user-unhandled exceptions](#BKMK_UserUnhandled) below.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> V Visual Basic spravuje ladicí program všechny chyby jako výjimky, i když používáte obslužné rutiny chyb ve stylu On Error.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Řekněte ladicímu programu, aby při vyvolání výjimky přerušil

Ladicí program může přerušit provádění v místě, kde je vyvolána výjimka, takže můžete zkoumat výjimku před vyvoláním obslužné rutiny.

V **okně Nastavení výjimky** ( Nastavení **> windows >**) rozbalte uzel pro kategorii výjimek, například **Výjimky modulu CLR (Common Language Runtime).** Potom zaškrtněte políčko pro konkrétní výjimku v rámci této kategorie, například **System.AccessViolationException**. Můžete také vybrat celou kategorii výjimek.

![Kontrola výjimky AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Konkrétní výjimky můžete najít  pomocí okna  Vyhledávání na panelu nástrojů Nastavení výjimky nebo pomocí vyhledávání vyfiltrovat konkrétní obory názvů (například **System.IO**).

Pokud v okně Nastavení  výjimky vyberete výjimku, provádění ladicího programu se přeruší bez ohledu na to, jestli je výjimka zpracována. Výjimka se teď nazývá výjimka první náhody. Tady je několik scénářů:

- V následující konzolové aplikaci jazyka C# vyvolá metoda Main výjimku **AccessViolationException** uvnitř `try/catch` bloku.

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

  Pokud je v **nastavení výjimky zaškrtnuté políčko AccessViolationException,** provádění se při spuštění tohoto kódu v ladicím programu přeruší na  `throw` řádku. Pak můžete pokračovat v provádění. Konzola by měla zobrazit oba řádky:

  ```cmd
  caught exception
  goodbye
  ```

  ale řádek se `here` nezobrazí.

- Konzolová aplikace jazyka C# odkazuje na knihovnu tříd s třídou, která má dvě metody. Jedna metoda vyvolá výjimku a zpracuje ji, zatímco druhá metoda vyvolá stejnou výjimku, ale nezpracuje ji.

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

  Pokud je v nastavení výjimky zaškrtnuté políčko **AccessViolationException,** provádění se při spuštění tohoto kódu v ladicím programu přeruší na řádku v obou případech  `throw` **ThrowHandledException()** i **ThrowUnhandledException().**

Pokud chcete obnovit výchozí nastavení výjimky, zvolte tlačítko Obnovit seznam **na výchozí** nastavení:

![Obnovení výchozích hodnot v nastavení výjimky](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Řekněte ladicímu programu, aby pokračoval u výjimek neošetřených uživatelem.

Pokud ladíte kód .NET nebo JavaScript pomocí [Pouze můj kód](../debugger/just-my-code.md), můžete ladicímu programu říct, aby se zabránilo přerušení výjimek, které nejsou zpracovány v uživatelském kódu, ale jsou zpracovány jinde.

1. V okně **Nastavení výjimky** otevřete místní nabídku tak, že kliknete pravým tlačítkem na popisek sloupce a pak vyberete Zobrazit sloupce **> Další akce.** (Pokud jste vypnuli **Pouze můj kód**, tento příkaz neuvidíte.) Zobrazí se třetí sloupec **s názvem Další** akce.

   ![Sloupec Další akce](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   U výjimky, která v tomto sloupci zobrazuje hodnotu **Continue** (Pokračovat), když se v uživatelském kódu v tomto sloupci neošetřeno, ladicí program pokračuje, pokud se tato výjimka nezpracovaná v uživatelském kódu, ale zpracovává se externě.

2. Pokud chcete toto nastavení pro konkrétní výjimku změnit, vyberte výjimku, kliknutím pravým tlačítkem zobrazte místní nabídku a v uživatelském kódu vyberte Continue **When Unhandled (Pokračovat** při neošetřené). Můžete také změnit nastavení pro celou kategorii výjimek, jako jsou například celé výjimky modulu Clr (Common Language Runtime).

   ![**Pokračovat při neošetřené práci v uživatelském kódu** – nastavení](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Například webové aplikace ASP.NET výjimky tak, že je převádí na stavový kód HTTP 500 ( Zpracování výjimek ve webovém rozhraní[API](/aspnet/web-api/overview/error-handling/exception-handling)ASP.NET ), který vám nemusí pomoct určit zdroj výjimky. V následujícím příkladu uživatelský kód provede volání , `String.Format()` které vyvolá <xref:System.FormatException> . Provádění se přeruší takto:

![Přerušení uživatelského&#45;neošetřené výjimce](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Přidání a odstranění výjimek

Výjimky můžete přidávat a odstraňovat. Pokud chcete odstranit typ výjimky z kategorie,  vyberte výjimku a zvolte odstranit vybranou výjimku z tlačítka seznamu (znaménko minus) na panelu nástrojů **Nastavení** výjimky. Nebo můžete kliknout pravým tlačítkem na výjimku a **v místní** nabídce vybrat Odstranit. Odstranění výjimky má stejný účinek jako zrušení výjimky, což znamená, že ladicí program se při vyvolání nezruší.

Přidání výjimky:

1. V okně **Nastavení výjimky** vyberte jednu z kategorií výjimek (například **Common Language Runtime).**

2. Zvolte **tlačítko Přidat výjimku do vybrané kategorie** (znaménko plus).

   ![**Přidání výjimky do vybrané kategorie**](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Zadejte název výjimky (například **System.UriTemplateMatchException**).

   ![Zadejte název výjimky.](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Výjimka se přidá do seznamu (v abecedním pořadí) a automaticky zaškrtne.

Pokud chcete přidat výjimku do kategorií Výjimky přístupu k paměti GPU, Výjimky modulu runtime JavaScript nebo Výjimky Win32, přidejte kód chyby a popis.

> [!TIP]
> Zkontrolujte pravopis! Okno **Nastavení výjimky** neschová existenci přidané výjimky. Pokud tedy napíšete **Sytem.UriTemplateMatchException**, získáte položku pro výjimku (a ne pro **System.UriTemplateMatchException**).

Nastavení výjimek se uchová v souboru .suo řešení, takže platí pro konkrétní řešení. Napříč řešeními nelze opakovaně používat konkrétní nastavení výjimek. Nyní jsou zachovány pouze přidané výjimky. odstraněné výjimky nejsou. Můžete přidat výjimku, zavřít a znovu otevřít řešení a výjimka tam bude i nadále. Pokud ale odstraníte výjimku a řešení zavřete nebo znovu otevřete, výjimka se znovu zobrazí.

Okno **Nastavení výjimky** podporuje obecné typy výjimek v jazyce C#, ale ne v Visual Basic. Pokud chcete přerušit výjimky, jako `MyNamespace.GenericException<T>` je , musíte přidat výjimku jako **MyNamespace.GenericException'1**. To znamená, že pokud jste vytvořili výjimku, jako je tento kód:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

K přidání výjimky do **nastavení výjimek můžete** použít předchozí postup:

![přidání obecné výjimky](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Přidání podmínek k výjimce

K nastavení **podmínek pro** výjimky použijte okno Nastavení výjimky. Aktuálně podporované podmínky zahrnují název nebo moduly, které se mají zahrnout nebo vyloučit pro výjimku. Když nastavíte názvy modulů jako podmínky, můžete se rozhodnout pro přerušení výjimky pouze u určitých modulů kódu. Můžete se také rozhodnout, že se vyhnete přerušení konkrétních modulů.

> [!NOTE]
> Přidávání podmínek k výjimce se podporuje od verze [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Přidání podmíněných výjimek:

1. Zvolte tlačítko **Upravit podmínky** v okně Nastavení výjimky nebo klikněte pravým tlačítkem na výjimku a zvolte **Upravit podmínky.**

   ![Podmínky pro výjimku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Pokud chcete k výjimce přidat další požadované podmínky, pro **každou** novou podmínku vyberte Přidat podmínku. Zobrazí se další řádky podmínky.

   ![Další podmínky pro výjimku](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Pro každý řádek podmínky zadejte název modulu a změňte seznam operátorů porovnání na **Rovná se** nebo **Není rovno**. Můžete zadat zástupné znaky ( **\\\*** ) v názvu a zadat více než jeden modul.

4. Pokud potřebujete odstranit podmínku, zvolte **X** na konci řádku podmínky.

## <a name="see-also"></a>Viz také

- [Pokračování v provádění po výjimce](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Postupy: Kontrola systémového kódu po výjimce](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Postupy: Použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
