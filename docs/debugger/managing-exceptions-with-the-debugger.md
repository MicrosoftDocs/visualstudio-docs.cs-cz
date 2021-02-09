---
title: Správa výjimek pomocí ladicího programu | Microsoft Docs
description: Naučte se, jak určit, které výjimky ladicí program přeruší, kde má být ladicí program přerušen a jak se zpracovávají přerušení.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: b594857b00ee233c186008efc9d0fba7d968a9bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893162"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Správa výjimek pomocí ladicího programu v aplikaci Visual Studio

Výjimka je indikace chybového stavu, který nastane při provádění programu. Můžete sdělit ladicímu programu, které výjimky nebo sady výjimek mají přerušit, a v jakém bodě chcete, aby ladicí program přerušil (to znamená pozastavení v ladicím programu). Po přerušení ladicího programu se zobrazí, kde byla vyvolána výjimka. Můžete také přidat nebo odstranit výjimky. S otevřeným řešením v aplikaci Visual Studio použijte příkaz **Debug > > nastavení výjimek** pro otevření okna **Nastavení výjimek** .

Poskytněte obslužné rutiny, které reagují na nejdůležitější výjimky. Potřebujete-li zjistit, jak přidat obslužné rutiny pro výjimky, přečtěte si téma [Oprava chyb psaním lepšího kódu jazyka C#](../debugger/write-better-code-with-visual-studio.md). Také se dozvíte, jak nakonfigurovat ladicí program tak, aby vždy přerušil provádění některých výjimek.

Pokud dojde k výjimce, ladicí program zapíše zprávu o výjimce do okna **výstup** . Může dojít k přerušení provádění v následujících případech:

- Je vyvolána výjimka, která není zpracována.
- Ladicí program je nakonfigurován k přerušení provádění před vyvoláním jakékoli obslužné rutiny.
- Nastavili jste [pouze můj kód](../debugger/just-my-code.md)a ladicí program je nakonfigurován k přerušení na jakékoli výjimce, která není zpracována v uživatelském kódu.

> [!NOTE]
> ASP.NET má obslužnou rutinu výjimky nejvyšší úrovně, která v prohlížeči zobrazuje chybové stránky. Nedojde k přerušení provádění, pokud není zapnuto **pouze můj kód** . Příklad naleznete v tématu [informování ladicího programu, aby pokračoval na neošetřených výjimkách](#BKMK_UserUnhandled) níže.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> V Visual Basic aplikaci spravuje ladicí program všechny chyby jako výjimky, a to i v případě, že používáte obslužné rutiny chyb ve stylu chyby.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Sdělit ladicímu programu přerušení při vyvolání výjimky

Ladicí program může přerušit provádění v místě, kde je vyvolána výjimka, takže je možné před vyvoláním obslužné rutiny ověřit výjimku.

V okně **nastavení výjimky** (**ladění > nastavení výjimek Windows >**) rozbalte uzel pro kategorii výjimek, například **výjimky modulu CLR (Common Language Runtime**). Pak zaškrtněte políčko pro konkrétní výjimku v této kategorii, například **System. AccessViolationException –**. Můžete také vybrat celou kategorii výjimek.

![Zaškrtnuté AccessViolationException –](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Konkrétní výjimky můžete najít pomocí okna **hledání** na panelu nástrojů **Nastavení výjimek** nebo pomocí hledání filtrovat konkrétní obory názvů (například **System.IO**).

Vyberete-li výjimku v okně **nastavení výjimky** , spuštění ladicího programu bude přerušeno všude, kde je vyvolána výjimka, bez ohledu na to, zda je zpracována. Nyní je výjimka označována jako výjimka první pravděpodobnost. Například tady je několik scénářů:

- V následující konzolové aplikaci jazyka C# vyvolá metoda Main **AccessViolationException –** uvnitř `try/catch` bloku.

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

  Pokud máte **AccessViolationException –** vrácení se změnami v **nastavení výjimky**, spuštění `throw` při spuštění tohoto kódu v ladicím programu bude přerušeno na řádku. Pak můžete pokračovat v provádění. Konzola by měla zobrazovat oba řádky:

  ```cmd
  caught exception
  goodbye
  ```

  ale nezobrazuje `here` řádek.

- Konzolová aplikace v jazyce C# odkazuje na knihovnu tříd se třídou, která má dvě metody. Jedna metoda vyvolá výjimku a zpracuje ji, zatímco druhá metoda vyvolá stejnou výjimku, ale nezpracovává ji.

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

  Zde je metoda Main () konzolové aplikace:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Pokud máte **AccessViolationException –** vrácení se změnami v **nastavení výjimky**, spuštění bude `throw` při spuštění tohoto kódu v ladicím programu přerušit na řádku v **ThrowHandledException ()** i **ThrowUnhandledException ()** .

Chcete-li obnovit výchozí nastavení výjimek, klikněte na tlačítko **Obnovit seznam na výchozí nastavení** :

![Obnovit výchozí hodnoty v nastavení výjimky](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Sdělte ladicímu programu, aby pokračoval na neošetřených výjimkách uživatele.

Pokud ladíte kód .NET nebo JavaScript pomocí [pouze můj kód](../debugger/just-my-code.md), můžete sdělit ladicímu programu, aby nedocházelo k přerušení výjimek, které nejsou zpracovány v uživatelském kódu, ale jsou zpracovávány jinde.

1. V okně **nastavení výjimky** otevřete místní nabídku tak, že kliknete pravým tlačítkem myši na popisek sloupce a pak vyberete **Zobrazit sloupce > další akce**. (Pokud jste vypnuli **pouze můj kód**, neuvidíte tento příkaz.) Zobrazí se třetí sloupec s názvem **Další akce** .

   ![Sloupec dalších akcí](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   V případě výjimky, která zobrazuje **pokračování v případě neošetřeného v uživatelském kódu** v tomto sloupci, ladicí program pokračuje, pokud tato výjimka nebude zpracována v uživatelském kódu, ale je zpracována externě.

2. Chcete-li toto nastavení změnit pro konkrétní výjimku, vyberte výjimku, kliknutím pravým tlačítkem myši zobrazte místní nabídku a vyberte možnost **pokračovat, pokud není v uživatelském kódu zpracována**. Můžete také změnit nastavení pro celou kategorii výjimek, například celé výjimky modulu CLR (Common Language Runtime).

   ![* * Pokračovat, pokud není ošetřená v uživatelském kódu * * nastavení](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Například webové aplikace ASP.NET zpracovávají výjimky jejich převedením na stavový kód HTTP 500 ([zpracování výjimek ve webovém rozhraní API ASP.NET](/aspnet/web-api/overview/error-handling/exception-handling)), které vám nemusí pomáhat určit zdroj výjimky. V následujícím příkladu kód uživatele provede volání metody `String.Format()` , která vyvolá výjimku <xref:System.FormatException> . Přerušení provádění následujícím způsobem:

![Přerušení na neošetřené výjimce uživatele&#45;](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Přidávání a odstraňování výjimek

Můžete přidat a odstranit výjimky. Chcete-li odstranit typ výjimky z kategorie, vyberte výjimku a zvolte **Odstranit vybranou výjimku z tlačítka seznam** (znaménko mínus) na panelu nástrojů **Nastavení výjimek** . Případně můžete kliknout pravým tlačítkem na výjimku a vybrat **Odstranit** z místní nabídky. Odstranění výjimky má stejný efekt jako nezaškrtnutá výjimka, což znamená, že ladicí program nebude při vyvolání přerušen.

Přidání výjimky:

1. V okně **nastavení výjimky** vyberte jednu z kategorií výjimek (například **modul CLR (Common Language Runtime**)).

2. Vyberte tlačítko **Přidat výjimku do vybrané kategorie** (znaménko plus).

   ![* * Přidat výjimku na tlačítko vybrané kategorie * *](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Zadejte název výjimky (například **System. UriTemplateMatchException**).

   ![Zadejte název výjimky.](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Výjimka je přidána do seznamu (v abecedním pořadí) a automaticky zaškrtnuto.

Chcete-li přidat výjimku do výjimek přístupu k paměti GPU, výjimek modulu runtime jazyka JavaScript nebo kategorií výjimek Win32, zahrňte kód chyby a popis.

> [!TIP]
> Zkontrolujte pravopis. Okno **nastavení výjimky** nekontroluje existenci přidané výjimky. Takže pokud zadáte **Sytem. UriTemplateMatchException**, dostanete položku pro tuto výjimku (a ne pro **System. UriTemplateMatchException**).

Nastavení výjimek jsou trvalá v souboru. suo řešení, takže se vztahují na konkrétní řešení. V rámci řešení nemůžete znovu použít specifická nastavení výjimek. Nyní jsou trvalé pouze přidané výjimky; odstraněné výjimky nejsou. Můžete přidat výjimku, zavřít a znovu otevřít řešení a výjimka bude stále k dispozici. Pokud ale odstraníte výjimku a zavřete nebo znovu otevřete řešení, výjimka se znovu zobrazí.

Okno **Nastavení výjimek** podporuje v jazyce C# obecné typy výjimek, ale ne v Visual Basic. Chcete-li přerušit na výjimkách `MyNamespace.GenericException<T>` , například, je nutné přidat výjimku jako **MyNamespace. GenericException ' 1**. To znamená, že pokud jste vytvořili výjimku, jako je tento kód:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Výjimku můžete přidat do **Nastavení výjimek** pomocí předchozího postupu:

![přidává se obecná výjimka.](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Přidat podmínky k výjimce

V okně **nastavení výjimky** můžete nastavit podmínky výjimek. Aktuálně podporované podmínky zahrnují názvy modulů, které se mají pro výjimku zahrnout nebo vyloučit. Nastavením názvů modulů jako podmínek můžete zvolit přerušení pro výjimku pouze v určitých modulech kódu. Můžete se také rozhodnout, že zabráníte přerušení určitých modulů.

> [!NOTE]
> Přidávání podmínek do výjimky je podporováno od začátku v [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Postup přidání podmíněných výjimek:

1. V okně nastavení výjimky klikněte na tlačítko **upravit podmínky** nebo klikněte pravým tlačítkem myši na výjimku a vyberte možnost **upravit podmínky**.

   ![Podmínky pro výjimku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Chcete-li pro výjimku přidat další požadované podmínky, vyberte **Přidat podmínku** pro každou novou podmínku. Zobrazí se další řádky podmínky.

   ![Další podmínky pro výjimku](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Pro každou řádek podmínky zadejte název modulu a změňte seznam relačních operátorů na **rovná** se nebo **není rovno**. Můžete zadat zástupné znaky ( **\\\*** ) v názvu pro určení více než jednoho modulu.

4. Pokud potřebujete podmínku odstranit, vyberte **X** na konci řádku podmínky.

## <a name="see-also"></a>Viz také

- [Pokračování v provádění po výjimce](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Postupy: Kontrola systémového kódu po výjimce](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Postupy: Použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
