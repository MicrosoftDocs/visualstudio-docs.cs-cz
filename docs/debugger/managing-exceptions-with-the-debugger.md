---
title: Správa výjimek pomocí ladicího programu | Dokumenty společnosti Microsoft
ms.custom: seodec18
ms.date: 10/09/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302152"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Správa výjimek pomocí ladicího programu v sadě Visual Studio

Výjimkou je označení chybového stavu, ke kterému dochází při provádění programu. Můžete sdělit ladicí program, které výjimky nebo sady výjimek přerušit, a v tomto okamžiku chcete ladicí program přerušit (to znamená pozastavit v ladicím programu). Když se ladicí program přeruší, ukáže, kde byla vyvolána výjimka. Můžete také přidat nebo odstranit výjimky. S otevřeným řešením v sadě Visual Studio otevřete okno **Nastavení výjimek** pomocí **funkce Ladění > Windows > Nastavení výjimek.**

Poskytněte obslužné rutiny, které reagují na nejdůležitější výjimky. Pokud potřebujete vědět, jak přidat obslužné rutiny pro výjimky, naleznete v [tématu Oprava chyb napsáním lepší kód C#](../debugger/write-better-code-with-visual-studio.md). Také se dozvíte, jak nakonfigurovat ladicí program vždy přerušit provádění pro některé výjimky.

Dojde-li k výjimce, ladicí program zapíše zprávu o výjimce do okna **Výstup.** Může přerušit provádění v následujících případech, kdy:

- Je vyvolána výjimka, která není zpracována.
- Ladicí program je nakonfigurován tak, aby přerušil provádění před vyvolání jakékoli obslužné rutiny.
- Nastavili jste [pouze můj kód](../debugger/just-my-code.md)a ladicí program je nakonfigurován tak, aby se přerušil při jakékoli výjimce, která není zpracována v uživatelském kódu.

> [!NOTE]
> ASP.NET má obslužnou rutinu výjimky nejvyšší úrovně, která zobrazuje chybové stránky v prohlížeči. Nepřeruší výkon, pokud není zapnutý **pouze můj kód.** Příklad naleznete v [tématu Tell ladicí program pokračovat na uživateleneošetřené výjimky](#BKMK_UserUnhandled) níže.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> V aplikaci jazyka Visual Basic ladicí program spravuje všechny chyby jako výjimky, i když používáte obslužné rutiny chyb y Na chybový styl.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Řekněte ladicímu programu, aby se přerušil při vyvolání výjimky

Ladicí program může přerušit provádění v místě, kde je vyvolána výjimka, takže můžete prozkoumat výjimku před vyvolání obslužné rutiny.

V okně **Nastavení výjimek** (**Ladění > nastavení > výjimek )** rozbalte uzel pro kategorii výjimek, například **Výjimky prostředí CLR**. Potom zaškrtněte políčko pro určitou výjimku v rámci této kategorie, například **System.AccessViolationException**. Můžete také vybrat celou kategorii výjimek.

![Zaškrtnuto AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Konkrétní výjimky můžete najít pomocí okna **Hledat** na panelu nástrojů **Nastavení výjimek** nebo pomocí funkce Hledat pro filtrování určitých oborů názvů (například **System.IO**).

Pokud vyberete výjimku v okně **Nastavení výjimky,** spuštění ladicího programu se přeruší všude tam, kde je výjimka vyvolána, bez ohledu na to, zda je zpracována. Nyní se výjimka nazývá výjimka první šance. Zde je například několik scénářů:

- V následující aplikaci konzoly C# Main metoda vyvolá `try/catch` **AccessViolationException** uvnitř bloku.

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

  Pokud máte **AccessViolationException** zaškrtnuto v **nastavení výjimky**, spuštění bude přerušit na `throw` řádku při spuštění tohoto kódu v ladicím programu. Potom můžete pokračovat v provádění. Konzola by měla zobrazit oba řádky:

  ```cmd
  caught exception
  goodbye
  ```

  ale nezobrazuje se `here` čára.

- Aplikace konzoly Jazyka C# odkazuje na knihovnu třídy s třídou, která má dvě metody. Jedna metoda vyvolá výjimku a zpracovává ji, zatímco druhá metoda vyvolá stejnou výjimku, ale nezpracovává ji.

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

  Zde je Main() metoda konzoly aplikace:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Pokud máte **AccessViolationException** zaškrtnuto v **nastavení výjimky**, spuštění se přeruší na `throw` řádku v obou **ThrowHandledException()** a **ThrowUnhandledException()** při spuštění tohoto kódu v ladicím programu.

Chcete-li obnovit výchozí nastavení výjimky, zvolte tlačítko **Obnovit seznam do výchozího nastavení:**

![Obnovit výchozí hodnoty v nastavení výjimek](../debugger/media/restoredefaultexceptions.png "Obnovit výchozí výjimky")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Řekněte ladicímu programu, aby pokračoval v neošetřených výjimkách uživatele.

Pokud ladíte kód .NET nebo JavaScript pomocí [kódu Just My Code](../debugger/just-my-code.md), můžete ladicímu programu sdělit, aby se zabránilo rozdělení výjimek, které nejsou zpracovány v uživatelském kódu, ale jsou zpracovány jinde.

1. V okně **Nastavení výjimky** otevřete místní nabídku klepnutím pravým tlačítkem myši na popisek sloupce a pak vyberte **Zobrazit sloupce > další akce**. (Pokud jste vypnuli **pouze můj kód**, tento příkaz se nezobrazí.) Zobrazí se třetí sloupec s názvem **Další akce.**

   ![Sloupec Další akce](../debugger/media/additionalactionscolumn.png "Sloupec AdditionalActionsColumn")

   Pro výjimku, která zobrazuje **Pokračovat při neošetřené v uživatelském kódu** v tomto sloupci ladicí program pokračuje, pokud tato výjimka není zpracována v uživatelském kódu, ale je zpracována externě.

2. Chcete-li změnit toto nastavení pro určitou výjimku, vyberte výjimku, klepnutím pravým tlačítkem myši zobrazte místní nabídku a v uživatelském kódu vyberte **pokračovat při neošetřeném zpracování**. Můžete také změnit nastavení pro celou kategorii výjimek, jako je například celý výjimky common language runtime).

   ![**Pokračovat při neošetřeném nastavení uživatelského kódu**](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Například ASP.NET webové aplikace zpracovávají výjimky jejich převedením na stavový kód HTTP 500 ([Zpracování výjimek v ASP.NET webovérozhraní API](/aspnet/web-api/overview/error-handling/exception-handling)), což vám nemusí pomoci určit zdroj výjimky. V níže uvedeném příkladu uživatelský `String.Format()` kód provede <xref:System.FormatException>volání, které vyvolá . Provádění přestávky takto:

![Přestávky na uživatele&#45;neošetřené výjimky](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Přidání a odstranění výjimek

Můžete přidávat a odstraňovat výjimky. Chcete-li odstranit typ výjimky z kategorie, vyberte výjimku a zvolte **Odstranit vybranou výjimku z** tlačítka seznamu (znaménko mínus) na panelu nástrojů **Nastavení výjimek.** Nebo můžete klepnout pravým tlačítkem myši na výjimku a vybrat **odstranit** z místní nabídky. Odstranění výjimky má stejný účinek jako s výjimkou nezaškrtnuté, což je, že ladicí program nebude přerušit, když je vyvolána.

Přidání výjimky:

1. V okně **Nastavení výjimky** vyberte jednu z kategorií výjimek (například **Common Language Runtime).**

2. Zvolte **tlačítko Přidat výjimku k vybrané kategorii** (znaménko plus).

   ![**Přidat výjimku do vybrané kategorie** tlačítka](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Zadejte název výjimky (například **System.UriTemplateMatchException**).

   ![Zadejte název výjimky.](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Výjimka je přidána do seznamu (v abecedním pořadí) a automaticky zaškrtnuta.

Chcete-li přidat výjimku do kategorií Výjimky přístupu k paměti GPU, výjimky javascriptového běhu nebo výjimky win32, uveďte kód chyby a popis.

> [!TIP]
> Zkontrolujte pravopis! Okno **Nastavení výjimek** nekontroluje existenci přidané výjimky. Pokud tedy zadáte **Sytem.UriTemplateMatchException**, získáte položku pro tuto výjimku (a ne pro **System.UriTemplateMatchException**).

Nastavení výjimky jsou trvalé v souboru .suo řešení, takže se vztahují na konkrétní řešení. V různých řešeních nelze znovu použít konkrétní nastavení výjimek. Nyní jsou zachovány pouze přidané výjimky; odstraněné výjimky nejsou. Můžete přidat výjimku, zavřít a znovu otevřít řešení a výjimka bude stále k dispozici. Ale pokud odstraníte výjimku a zavřete nebo znovu otevřete řešení, výjimka se znovu zobrazí.

Okno **Nastavení výjimek** podporuje obecné typy výjimek v jazyce C#, ale ne v jazyce Visual Basic. Chcete-li přerušit `MyNamespace.GenericException<T>`výjimky, jako je , musíte přidat výjimku jako **MyNamespace.GenericException'1**. To znamená, že pokud jste vytvořili výjimku, jako je tento kód:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Výjimku můžete přidat do **nastavení výjimek** pomocí předchozího postupu:

![přidání obecné výjimky](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Přidání podmínek k výjimce

Okno **Nastavení výjimek** slouží k nastavení podmínek výjimek. Aktuálně podporované podmínky zahrnují názvy modulů, které mají být zahrnuty nebo vyloučeny pro výjimku. Nastavením názvů modulů jako podmínek můžete tuto výjimku přerušit pouze u určitých modulů kódu. Můžete se také rozhodnout, aby se zabránilo lámání na konkrétní moduly.

> [!NOTE]
> Přidání podmínek k výjimce je podporováno od začátku aplikace [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Přidání podmíněných výjimek:

1. V okně Nastavení výjimek zvolte tlačítko **Upravit podmínky** nebo klepněte pravým tlačítkem myši na výjimku a zvolte **Upravit podmínky**.

   ![Podmínky pro výjimku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Chcete-li k výjimce přidat další požadované podmínky, vyberte **přidat podmínku** pro každou novou podmínku. Zobrazí se další řádky podmínky.

   ![Dodatečné podmínky pro výjimku](../debugger/media/extraconditionsforanexception.png "ExtraconditionsforanException")

3. Pro každý řádek podmínky zadejte název modulu a změňte seznam **operátorů** porovnání na Rovná se nebo **Nerovná**. Můžete zadat zástupné**\\**znaky ( ) v názvu zadat více než jeden modul.

4. Pokud potřebujete odstranit podmínku, zvolte **X** na konci řádku podmínky.

## <a name="see-also"></a>Viz také

- [Pokračování ve spuštění po výjimce](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Postupy: Kontrola systémového kódu po výjimce](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Postupy: Použití nativních kontrol za běhu](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Použití kontrol za běhu bez knihovny za běhu C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
