---
title: Návod k analýze spravovaného kódu pro vady kódu | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 79855f6915bbb0ed15bfd09f99fab0403290f09e
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448715"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Návod: použití statické analýzy kódu k vyhledání vad kódu

V tomto návodu budete analyzovat spravovaný projekt pro vady kódu pomocí nástroje Analýza kódu starší verze.

Tento článek vás provede procesem použití starší verze analýzy k analýze sestavení spravovaného kódu .NET pro účely souladu s pokyny pro návrh .NET.

## <a name="create-a-class-library"></a>Vytvoření knihovny tříd

1. Otevřete Visual Studio a vytvořte nový projekt ze šablony **knihovny tříd (.NET Framework)** .

1. Pojmenujte projekt **CodeAnalysisManagedDemo**.

1. Po vytvoření projektu otevřete soubor *Class1.cs* .

1. Existující text v Class1.cs nahraďte následujícím kódem:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Uložte soubor Class1.cs.

## <a name="analyze-the-project-for-code-defects"></a>Analyzovat chyby kódu v projektu

1. Vyberte projekt CodeAnalysisManagedDemo v **Průzkumník řešení**.

2. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

   Zobrazí se stránka vlastnosti CodeAnalysisManagedDemo.

3. Klikněte na kartu **Analýza kódu** .

::: moniker range="vs-2017"

4. Ujistěte se, že je vybraná **možnost povolit analýzu kódu při sestavení** .

5. V rozevíracím seznamu **Spustit tuto sadu pravidel** vyberte možnost **Microsoft všechna pravidla**.

::: moniker-end

::: moniker range=">=vs-2019"

4. Ujistěte se, že je v sekci **binární analyzátory** vybraná možnost **Spustit při sestavování** .

5. V rozevíracím seznamu **aktivní pravidla** vyberte **Microsoft všechna pravidla**.

::: moniker-end

6. V nabídce **soubor** klikněte na příkaz **Uložit vybrané položky**a poté zavřete stránky vlastnosti.

7. V nabídce **sestavení** klikněte na příkaz **sestavit CodeAnalysisManagedDemo**.

    Upozornění sestavení projektu CodeAnalysisManagedDemo se zobrazují v oknech **Seznam chyb** a **výstup** .

## <a name="correct-the-code-analysis-issues"></a>Opravte potíže s analýzou kódu

1. V nabídce **zobrazení** vyberte možnost **Seznam chyb**.

    V závislosti na zvoleném profilu vývojáře možná budete muset v nabídce **zobrazení** Ukázat na **jiné okna** a pak vybrat **Seznam chyb**.

1. V **Průzkumník řešení**vyberte možnost **Zobrazit všechny soubory**.

1. Rozbalte uzel vlastnosti a pak otevřete soubor *AssemblyInfo.cs* .

1. Upozornění můžete opravit pomocí následujících tipů:

   [CA1014: Označte sestavení pomocí CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): přidejte kód `[assembly: CLSCompliant(true)]` na konec souboru AssemblyInfo.cs.

   [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): přidejte konstruktor `public demo (String s) : base(s) { }` do třídy `demo`.

   [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): přidejte konstruktor `public demo (String s, Exception e) : base(s, e) { }` do třídy `demo`.

   [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): přidejte konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` do ukázky třídy. Také budete muset přidat příkaz `using` pro <xref:System.Runtime.Serialization?displayProperty=fullName>.

   [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): přidejte konstruktor `public demo () : base() { }` do třídy `demo`.

   [CA1709: identifikátory by měly být správně použita](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Změňte velikost písmen oboru názvů `testCode` na `TestCode`.

   [CA1709: identifikátory by se měly použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Změňte název členu na `Demo`.

   [CA1709: identifikátory by se měly použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Změňte název členu na `Item`.

   [CA1710: identifikátory by měly mít správnou příponu](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Změňte název třídy a její konstruktory na `DemoException`.

   [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237.md): přidejte atribut `[Serializable ()]` do třídy `demo`.

   [CA2210: sestavení musí mít platné silné názvy](../code-quality/ca2210.md): Sign ' CodeAnalysisManagedDemo ' se silným názvem klíče:

   1. V nabídce **projekt** vyberte **vlastnosti CodeAnalysisManagedDemo**.

      Zobrazí se vlastnosti projektu.

   1. Klikněte na kartu **podepisování** .

   1. Zaškrtněte políčko **podepsat sestavení** .

   1. V seznamu **Vyberte soubor klíče s názvem řetězce** vyberte **\<New >** .

      Zobrazí se dialogové okno **vytvořit klíč se silným názvem** .

   1. Jako **název souboru klíče**zadejte **testkey**.

   1. Zadejte heslo a klikněte na **tlačítko OK**.

   1. V nabídce **soubor** klikněte na příkaz **Uložit vybrané položky**a poté zavřete stránky vlastností.

   Až všechny změny dokončíte, soubor Class1.cs by měl vypadat takto:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Znovu sestavte projekt.

## <a name="exclude-code-analysis-warnings"></a>Upozornění analýzy kódu vyloučení

1. Pro každé ze zbývajících upozornění proveďte následující:

    1. Vyberte upozornění v **Seznam chyb**.

    1. V nabídce kliknutím pravým tlačítkem myši (kontextová nabídka) vyberte možnost **potlačit** > **v souboru potlačení**.

1. Znovu sestavte projekt.

     Projekt se vytváří bez upozornění a chyb.

## <a name="see-also"></a>Viz také:

[Analýza kódu pro spravovaný kód](../code-quality/code-analysis-for-managed-code-overview.md)
