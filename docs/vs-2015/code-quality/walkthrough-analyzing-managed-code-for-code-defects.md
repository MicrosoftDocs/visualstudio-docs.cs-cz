---
title: 'Návod: Analýza spravovaného kódu na výskyt závad kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0b9d6aba5997182578b43ac9edd3c889bcfc365e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912887"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Návod: Analýza spravovaného kódu na výskyt závad v kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto podrobném návodu analyzovat spravovaný projekt závad v kódu pomocí nástroje Analýza kódu.  
  
 Tento návod vás postupně provede procesem pomocí analýzy kódu pro analýzu sestavení .NET spravovat kód pro soulad s pokyny návrhu rozhraní Microsoft .NET Framework.  
  
 V tomto podrobném návodu můžete:  
  
-   Analýza a opravte upozornění vad kódu.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>Vytvoření knihovny tříd  
  
#### <a name="to-create-a-class-library"></a>Chcete-li vytvořit knihovnu tříd  
  
1.  Na **souboru** nabídku [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], klikněte na tlačítko **nový** a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogovém okně **typy projektů**, klikněte na tlačítko **Visual C#**.  
  
3.  V části **šablony**vyberte **knihovny tříd**.  
  
4.  V **název** textového pole, typ **CodeAnalysisManagedDemo** a potom klikněte na tlačítko **OK**.  
  
5.  Po vytvoření projektu otevřete soubor Class1.cs.  
  
6.  Nahraďte existující text v Class1.cs následujícím kódem:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Uložte soubor Class1.cs.  
  
## <a name="analyze-the-project"></a>Analýza projektu  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>K analýze spravovaných projektů závad v kódu  
  
1.  Vyberte projekt CodeAnalysisManagedDemo v **Průzkumníka řešení**.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
     Zobrazí se stránka Vlastnosti CodeAnalysisManagedDemo.  
  
3.  Klikněte na tlačítko **úloze CodeAnalysis**.  
  
4.  Ujistěte se, že **povolit analýzu kódu na sestavení (definuje konstantu CODE_ANALYSIS**) je zaškrtnuté políčko.  
  
5.  Z **spustit tuto sadu pravidel** rozevíracího seznamu vyberte **všechna pravidla společnosti Microsoft**.  
  
6.  Na **souboru** nabídky, klikněte na tlačítko **uložit vybrané položky**a pak zavřete ManagedDemo stránky vlastností.  
  
7.  Na **sestavení** nabídky, klikněte na tlačítko **sestavení ManagedDemo**.  
  
     Upozornění sestavení projektu CodeAnalysisManagedDemo jsou hlášeny v **analýzy kódu** a **výstup** systému windows.  
  
     Pokud **analýzy kódu** okno nezobrazí, na **analyzovat** nabídce zvolte **Windows** a potom **zvolte analýzy kódu**.  
  
## <a name="correct-the-code-analysis-issues"></a>Opravte problémy s analýzou kódu  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Chcete-li opravit porušení pravidel analýzy kódu  
  
1.  Na **zobrazení** nabídky, klikněte na tlačítko **seznam chyb**.  
  
     V závislosti na profil pro vývojáře, který jste zvolili, možná budete muset odkazovat na **ostatní Windows** na **zobrazení** nabídky a pak klikněte na tlačítko **seznam chyb**.  
  
2.  V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory**.  
  
3.  Dále rozbalte uzel vlastnosti a pak otevřete soubor AssemblyInfo.cs.  
  
4.  Chcete-li opravit upozornění použijte následující:  
  
- [CA1014: Označte sestavení pomocí atributu CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'ukázka' by měla být označena CLSCompliantAttribute a jeho hodnota by měla mít hodnotu true.  
  
  -   Přidejte kód `using``System;` soubor AssemblyInfo.cs.  
  
       V dalším kroku přidejte kód `[assembly: CLSCompliant(true)]` na konec souboru AssemblyInfo.cs.  
  
       Sestavte projekt znovu.  
  
- [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: přidejte následující konstruktor k této třídě: veřejné demo(String)  
  
  -   Přidejte konstruktor `public demo (String s) : base(s) { }` do třídy `demo`.  
  
- [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: přidejte následující konstruktor k této třídě: veřejné ukázkové (String, výjimka)  
  
  -   Přidejte konstruktor `public demo (String s, Exception e) : base(s, e) { }` do třídy `demo`.  
  
- [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: přidejte následující konstruktor k této třídě: chráněné ukázka (SerializationInfo, StreamingContext)  
  
  -   Přidejte kód `using System.Runtime.Serialization;` na začátek souboru Class1.cs.  
  
       V dalším kroku přidejte konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       Sestavte projekt znovu.  
  
- [CA1032: Implementujte standardní konstruktory výjimky](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: přidejte následující konstruktor k této třídě: veřejné demo()  
  
  -   Přidejte konstruktor `public demo () : base() { }` do třídy `demo` **.**  
  
       Sestavte projekt znovu.  
  
- [CA1709: Identifikátory by měly být správně formátováno](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Opravte použití malých a velkých oboru názvů názvu 'testCode' pomocí změny na "TestCode".  
  
  -   Změna velikosti písmen názvů `testCode` k `TestCode`.  
  
- [CA1709: Identifikátory by měly být správně formátováno](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Opravte použití malých a velkých název typu 'ukázku"změnou"Ukázka".  
  
  -   Název členu, který chcete změnit `Demo`.  
  
- [CA1709: Identifikátory by měly být správně formátováno](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Opravte použití malých a velkých název člena 'item' pomocí změny na "Položka".  
  
  -   Název členu, který chcete změnit `Item`.  
  
- [CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: přejmenování 'testCode.demo"tak, že končí 'Exception'.  
  
  -   Změnit název třídy a jejích konstruktorů k `DemoException`.  
  
- [CA2210: Sestavení by měly mít platné silné názvy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): "ManagedDemo" podepsat klíče silného názvu.  
  
  -   Na **projektu** nabídky, klikněte na tlačítko **ManagedDemo vlastnosti**.  
  
       Zobrazí vlastnosti projektu.  
  
       Klikněte na tlačítko **podepisování**.  
  
       Vyberte **podepsat sestavení** zaškrtávací políčko.  
  
       V **vybrat soubor klíče název řetězce** seznamu vyberte  **\<nový … >**.  
  
       **Vytvořit klíč se silným názvem** zobrazí se dialogové okno.  
  
       V **název souboru klíče**, zadejte TestKey.  
  
       Zadejte heslo a potom klikněte na tlačítko **OK**.  
  
       Na **souboru** nabídky, klikněte na tlačítko **uložit vybrané položky**a pak zavřete stránku vlastností.  
  
       Sestavte projekt znovu.  
  
- [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Přidejte atribut [Serializable] na typ 'ukázka' protože tento typ implementuje ISerializable.  
  
  -   Přidat `[Serializable ()]` atribut třídy `demo`.  
  
       Sestavte projekt znovu.  
  
  Po dokončení změny souboru Class1.cs by měl vypadat nějak takto:  
  
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
  
## <a name="exclude-code-analysis-warnings"></a>Vyloučit upozornění analýzy kódu  
  
#### <a name="to-exclude-code-defect-warnings"></a>Chcete-li vyloučit upozornění vad kódu  
  
1. Pro každý zbývající upozornění postupujte takto:  
  
   1. V okně analýzy kódu vyberte upozornění.  
  
   2. Zvolte **akce**, klikněte na tlačítko **potlačit zprávu**a klikněte na tlačítko **v souboru potlačení projektu**.  
  
      Další informace najdete v tématu [postupy: potlačení upozornění použitím položky nabídky](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. Sestavte projekt znovu.  
  
    Projekt se sestaví bez žádná upozornění ani chyby.



