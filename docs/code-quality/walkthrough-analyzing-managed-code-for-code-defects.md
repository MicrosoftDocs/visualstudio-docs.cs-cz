---
title: Návod analýza spravovaného kódu na výskyt závad v kódu | Microsoft Docs
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 49c122e5cf22e9290f6dab1d45539887c68c01bd
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117716"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Návod: Analýza spravovaného kódu pro kód vady

V tomto návodu analyzujete spravovaný projekt pro defekty kódu pomocí nástroje Analýza kódu.

Tento názorný postup vás provede procesem použití analýzy kódu pro analýzu sestavení kódu vaší spravované rozhraní .NET pro shodu s pokyny pro návrh rozhraní Microsoft .NET Framework.

## <a name="create-a-class-library"></a>Vytvoření knihovny tříd

### <a name="to-create-a-class-library"></a>K vytvoření knihovny tříd

1. Na **soubor** nabídce zvolte **nový** > **projektu**.

1. V **nový projekt** dialogové okno, rozbalte seznam **nainstalovaná** > **Visual C#** a potom zvolte **Windows Desktop**.

1. Vyberte **knihovny tříd (rozhraní .NET Framework)** šablony.

1. V **název** textového pole, typ **CodeAnalysisManagedDemo** a pak klikněte na **OK**.

1. Po vytvoření projektu, otevřete *Class1.cs* souboru.

1. Nahradí existující text v Class1.cs následujícím kódem:

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

## <a name="analyze-the-project"></a>Analýza projektu

### <a name="to-analyze-a-managed-project-for-code-defects"></a>K analýze spravovaný projekt pro defekty kódu

1. Vyberte projekt CodeAnalysisManagedDemo v **Průzkumníku řešení**.

1. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

     Zobrazí se stránka vlastností CodeAnalysisManagedDemo.

1. Vyberte **analýza kódu** kartě.

1. Ujistěte se, že **povolit analýza kódu při sestavování** je zaškrtnuté.

1. Z **spuštění této sady pravidel** rozevíracího seznamu vyberte **všechna pravidla Microsoft**.

1. Na **soubor** nabídky, klikněte na tlačítko **uložit vybrané položky**a pak zavřete vlastnosti stránky.

1. Na **sestavení** nabídky, klikněte na tlačítko **sestavení CodeAnalysisManagedDemo**.

    Upozornění sestavení projektu CodeAnalysisManagedDemo se zobrazují v **seznam chyb** a **výstup** systému windows.

## <a name="correct-the-code-analysis-issues"></a>Opravte problémy analýzy kódu

### <a name="to-correct-code-analysis-rule-violations"></a>Chcete-li opravit porušení pravidel analýzy kódu

1. Na **zobrazení** nabídce zvolte **seznam chyb**.

    V závislosti na vývojáře profil, který jste zvolili, možná budete muset přejděte na příkaz **ostatní okna** na **zobrazení** nabídce a potom zvolte **seznam chyb**.

1. V **Průzkumníku řešení**, zvolte **zobrazit všechny soubory**.

1. Rozbalte uzel vlastnosti a pak otevřete *AssemblyInfo.cs* souboru.

1. Opravte upozornění pomocí následující tipy:

   [CA1014: Označte sestavení pomocí atributu CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'ukázku' by měl být označen s CLSCompliantAttribute a by měl mít hodnotu true.

   1. Přidejte kód `using System;` AssemblyInfo.cs souboru.

   1. Dál přidejte kód `[assembly: CLSCompliant(true)]` na konec souboru AssemblyInfo.cs.

   [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: přidejte následující konstruktor do této třídy: veřejné demo(String)

   1. Přidat konstruktoru `public demo (String s) : base(s) { }` k třídě `demo`.

   [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: přidejte následující konstruktor do této třídy: veřejné ukázku (řetězec, výjimka)

   1. Přidat konstruktoru `public demo (String s, Exception e) : base(s, e) { }` k třídě `demo`.

   [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: přidejte následující konstruktor do této třídy: chráněný ukázku (položku SerializationInfo, StreamingContext)

   1. Přidejte kód `using System.Runtime.Serialization;` na začátek souboru Class1.cs.

   1. Dál přidejte konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: přidejte následující konstruktor do této třídy: veřejné demo()

   1. Přidat konstruktoru `public demo () : base() { }` k třídě `demo` **.**

   [CA1709: Identifikátory by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Opravte malá a velká písmena název oboru názvů 'testCode' změnou 'TestCode'.

   1. Změnit malá a velká písmena oboru názvů `testCode` k `TestCode`.

   [CA1709: Identifikátory by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Opravte malá a velká písmena název typu 'ukázku' změnou 'Ukázku'.

   1. Změňte název člena na `Demo`.

   [CA1709: Identifikátory by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Opravte malá a velká písmena název člena 'item' změnou 'Item'.

   1. Změňte název člena na `Item`.

   [CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: přejmenování 'testCode.demo' končit 'Výjimka'.

   1. Změnit název třídy a pro její konstruktory `DemoException`.

   [CA2210: Sestavení by měly mít platné silné názvy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'CodeAnalysisManagedDemo' podepsat složitý název klíče.

   1. Na **projektu** nabídce zvolte **CodeAnalysisManagedDemo vlastnosti**.

      Zobrazí vlastnosti projektu.

   1. Vyberte **podpisování** kartě.

   1. Vyberte **podepsání sestavení** zaškrtávací políčko.

   1. V **vyberte soubor klíče název řetězec** seznamu, vyberte  **\<nová... >**.

      **Vytvořit klíč se silným názvem** zobrazí se dialogové okno.

   1. V **název souboru klíče**, zadejte TestKey.

   1. Zadejte heslo a potom zvolte **OK**.

   1. Na **soubor** nabídce zvolte **uložit vybrané položky**a pak zavřete stránky vlastností.

   [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: přidání atributu [Serializable] na typ 'ukázku, protože tento typ implementuje vlastnost ISerializable.

   1. Přidat `[Serializable ()]` atribut třídy `demo`.

   Po dokončení změny souboru Class1.cs by měl vypadat asi takto:

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

## <a name="exclude-code-analysis-warnings"></a>Vyloučit upozornění analýzy kódu

### <a name="to-exclude-code-defect-warnings"></a>Vyloučit upozornění vadou kódu

1. Pro každý zbývající upozornění, postupujte takto:

    1. Vyberte upozornění v **seznam chyb**.

    1. V nabídce klikněte pravým tlačítkem nebo kontextu zvolte **potlačit** > **v souboru potlačení**.

1. Znovu sestavte projekt.

     Sestavení projektu bez žádná upozornění ani chyby.

## <a name="see-also"></a>Viz také:

[Analýza kódu pro spravovaný kód](../code-quality/code-analysis-for-managed-code-overview.md)