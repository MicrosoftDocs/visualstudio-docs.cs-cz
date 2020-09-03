---
title: 'Návod: Analýza spravovaného kódu pro vady kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609324"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Návod: Analýza spravovaného kódu na výskyt závad v kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu analyzujete spravovaný projekt pro vady kódu pomocí nástroje Analýza kódu.

 Tento návod vás provede procesem použití analýzy kódu k analýze sestavení spravovaného kódu .NET pro účely souladu s pokyny pro návrh Microsoft .NET Frameworke.

 V tomto návodu:

- Analyzujte a opravte upozornění na vady kódu.

## <a name="prerequisites"></a>Předpoklady

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].

## <a name="create-a-class-library"></a>Vytvoření knihovny tříd

#### <a name="to-create-a-class-library"></a>Vytvoření knihovny tříd

1. V nabídce **soubor** v aplikaci [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] klikněte na **Nový** a pak klikněte na **projekt**.

2. V dialogovém okně **Nový projekt** , v části **typy projektů**klikněte na možnost **Visual C#**.

3. V části **šablony**vyberte **Knihovna tříd**.

4. Do textového pole **název** zadejte **CodeAnalysisManagedDemo** a pak klikněte na **OK**.

5. Po vytvoření projektu otevřete soubor Class1.cs.

6. Existující text v Class1.cs nahraďte následujícím kódem:

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Uložte soubor Class1.cs.

## <a name="analyze-the-project"></a>Analyzovat projekt

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Analýza spravovaného projektu pro vady kódu

1. Vyberte projekt CodeAnalysisManagedDemo v **Průzkumník řešení**.

2. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

     Zobrazí se stránka vlastnosti CodeAnalysisManagedDemo.

3. Klikněte na **CodeAnalysis**.

4. Ujistěte se, že je zaškrtnuté políčko  **Povolit analýzu kódu při sestavení (definuje CODE_ANALYSIS konstanta**).

5. V rozevíracím seznamu **Spustit tuto sadu pravidel** vyberte možnost **Microsoft všechna pravidla**.

6. V nabídce **soubor** klikněte na příkaz **Uložit vybrané položky**a poté zavřete stránky vlastností ManagedDemo.

7. V nabídce **sestavení** klikněte na příkaz **sestavit ManagedDemo**.

     Upozornění sestavení projektu CodeAnalysisManagedDemo jsou uvedena v oknech **Code Analysis** and **Output** .

     Pokud se okno **Analýza kódu** nezobrazí, v nabídce **analyzovat** zvolte **okna** a pak **Zvolte Analýza kódu**.

## <a name="correct-the-code-analysis-issues"></a>Opravte potíže s analýzou kódu

#### <a name="to-correct-code-analysis-rule-violations"></a>Oprava porušení pravidel pro analýzu kódu

1. V nabídce **zobrazení** klikněte na příkaz **Seznam chyb**.

     V závislosti na zvoleném profilu vývojáře možná budete muset v nabídce **zobrazení** Ukázat na **jiné okna** a pak kliknout na **Seznam chyb**.

2. V **Průzkumník řešení**klikněte na **Zobrazit všechny soubory**.

3. Dále rozbalte uzel vlastnosti a pak otevřete soubor AssemblyInfo.cs.

4. K opravě upozornění použijte následující:

- [CA1014: Označte sestavení pomocí CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: ' Demo ' by měl být označený CLSCompliantAttribute a jeho hodnota by měla být true.

  - Přidejte kód `using``System;` do souboru AssemblyInfo.cs.

       Dále přidejte kód `[assembly: CLSCompliant(true)]` na konec souboru AssemblyInfo.cs.

       Znovu sestavte projekt.

- [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: přidejte do této třídy následující konstruktor: public demo (String)

  - Přidejte konstruktor `public demo (String s) : base(s) { }` do třídy `demo` .

- [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: přidejte do této třídy následující konstruktor: public demo (řetězec, výjimka)

  - Přidejte konstruktor `public demo (String s, Exception e) : base(s, e) { }` do třídy `demo` .

- [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: přidejte do této třídy následující konstruktor: protected demo (SerializationInfo, StreamingContext).

  - Přidejte kód `using System.Runtime.Serialization;` na začátek souboru Class1.cs.

       Dále přidejte konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Znovu sestavte projekt.

- [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: přidejte do této třídy následující konstruktor: public demo ()

  - Přidejte konstruktor `public demo () : base() { }` do třídy `demo` **.**

       Znovu sestavte projekt.

- [CA1709: identifikátory by se měly použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. pojmenování: Opravte velikost písmen oboru názvů TestCode, a to změnou na TestCode.

  - Změňte velikost písmen oboru názvů `testCode` na `TestCode` .

- [CA1709: identifikátory by se měly použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. pojmenování: Opravte velká a malá písmena typu název ' Demo ', a to změnou na ' Demo '.

  - Změňte název člena na `Demo` .

- [CA1709: identifikátory by měly být správně použita](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. pojmenování: Opravte velikost písmen členů názvu ' Item ' změnou na ' Item '.

  - Změňte název člena na `Item` .

- [CA1710: identifikátory by měly mít správnou příponu](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. pojmenování: přejmenovat ' TestCode. Demo ' na konec ' Exception '.

  - Změňte název třídy a jejích konstruktorů na `DemoException` .

- [CA2210: sestavení by měly mít platné silné názvy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Podepište ' ManagedDemo ' pomocí klíče silného názvu.

  - V nabídce **projekt** klikněte na **vlastnosti ManagedDemo**.

       Zobrazí se vlastnosti projektu.

       Klikněte na **podepisování**.

       Zaškrtněte políčko **podepsat sestavení** .

       V seznamu **Zvolte soubor klíče s názvem řetězce** vyberte **\<New…>** .

       Zobrazí se dialogové okno **vytvořit klíč se silným názvem** .

       Do pole **název souboru klíče**zadejte TestKey.

       Zadejte heslo a klikněte na **OK**.

       V nabídce **soubor** klikněte na příkaz **Uložit vybrané položky**a poté zavřete stránky vlastností.

       Znovu sestavte projekt.

- [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: přidejte atribut [serializovatelný] do typu demo, protože tento typ implementuje ISerializable.

  - Přidejte `[Serializable ()]` atribut do třídy `demo` .

       Znovu sestavte projekt.

  Až změny dokončíte, soubor Class1.cs by měl vypadat takto:

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>Upozornění analýzy kódu vyloučení

#### <a name="to-exclude-code-defect-warnings"></a>Vyloučení upozornění na vady kódu

1. Pro každé ze zbývajících upozornění proveďte následující:

   1. V okně Analýza kódu vyberte upozornění.

   2. Zvolte **Akce**, zvolte možnost potlačit **zprávu**a pak zvolte možnost **v souboru potlačení projektu**.

      Další informace naleznete v tématu [How to: potlačení upozornění pomocí položky nabídky](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. Znovu sestavte projekt.

    Projekt se vytváří bez upozornění a chyb.
