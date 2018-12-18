---
title: Psaní kódu v řešeních pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9773c06293f189e572ef84e9b10f45a1ca5d5d8
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670985"
---
# <a name="write-code-in-office-solutions"></a>Psaní kódu v řešeních pro systém Office
  Existují některé aspekty psaní kódu v projektech Office, které se liší od ostatních typů projektů v sadě Visual Studio. Mnohé z těchto rozdílů jsou týkající se způsobu, jakým Office – objektové modely jsou přístupné pro spravovaný kód. Další rozdíly v návrhu projektů Office souvisejí.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="managed-code-and-office-programming"></a>Spravovaný kód a programování pro systém Office  
 Klíčové technologie, která umožňuje vytváření integrované řešení Microsoft Office je automatizace, která je součástí technologie modelu COM (Component Object). Automation vám umožní použít kód k vytvoření a řízení objektů softwaru zveřejněné ve všech aplikacích, knihovny DLL, nebo ovládacího prvku ActiveX, který podporuje odpovídající programových rozhraní.  
  
### <a name="understand-primary-interop-assemblies"></a>Vysvětlení primárních sestavení vzájemné spolupráce  
 Aplikace Microsoft Office vystavit většina jejich funkcí automatizace. Spravovaný kód (například Visual Basic nebo C#) však nelze použít přímo pro automatizaci aplikací Office. K automatizaci aplikace Office pomocí spravovaného kódu, musíte použít Office primární sestavení interop (PIA). Primární spolupracující sestavení povolit spravovanému kódu pracovat s modelem objektů založené na modelu COM z aplikací Office.  
  
 Má každá aplikace Microsoft Office PIA. Při vytváření projektu pro Office v sadě Visual Studio se do projektu automaticky přidá odkaz na příslušný PIA. K automatizaci funkcí ostatních aplikací Office z projektu, musíte přidat odkaz na příslušný PIA ručně. Další informace najdete v tématu [jak: aplikace Office cílové primárních sestaveních vzájemné spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Použít sestavení primární spolupráce v době návrhu a běhu  
 PIA pro systém Office nainstalována a zaregistrována v globální mezipaměti sestavení na vašem vývojovém počítači provádět většinu vývojářských úkolů musíte mít. Další informace najdete v tématu [konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Sestavení PIA sady Office nejsou vyžadovány v počítačích koncových uživatelů ke spuštění řešení pro systém Office, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Další informace najdete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="use-types-in-primary-interop-assemblies"></a>Použít typy v sestavení primární spolupráce  
 Sestavení PIA sady Office obsahovat kombinaci typů, které zveřejňují objektový model aplikace Office a další infrastrukturu typy, které nejsou určeny k použití přímo ve vašem kódu. Přehled typů v sestavení PIA sady Office naleznete v tématu [přehled třídy a rozhraní v primární spolupracující sestavení Office](/previous-versions/office/office-12/ms247299\(v\=office.12\)).  
  
 Vzhledem k tomu, že typy v sestavení PIA sady Office odpovídají typům v modelech objektů založené na modelu COM, je často způsob, jak používat tyto typy liší od jiné spravované typy. Způsob volání metody, které mají volitelné parametry v sestavení primární spolupráce Office, například závisí na programovací jazyk, který používáte ve vašem projektu. Další informace naleznete v následujících tématech:  
  
-   [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md).  
  
-   [Pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md).  
  
## <a name="program-model-of-office-projects"></a>Model program projektů Office  
 Všechny projekty Office zahrnují jeden nebo více generované třídy, které poskytují vstupní bod pro kód. Tyto třídy také poskytují přístup k objektovému modelu hostitelské aplikace a přístup k funkcím, jako jsou podokna akcí a vlastních podoken úloh.  
  
### <a name="understand-the-generated-classes"></a>Vysvětlení vygenerovaných tříd  
 V projekty na úrovni dokumentu pro Excel a Word generované třídy vypadá podobně jako objekt nejvyšší úrovně v objektovém modelu aplikace. Například generované `ThisDocument` třídu v projektu dokumentu aplikace Word poskytuje stejné členy jako <xref:Microsoft.Office.Interop.Word.Document> třídy v objektovém modelu aplikace Word. Další informace o vygenerovaných tříd v projektech na úrovni dokumentu naleznete v tématu [programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md).  
  
 Projekty doplňků VSTO poskytují generovanou třídu s názvem `ThisAddIn`. Tato třída není vypadat podobně jako na třídu v objektovém modelu hostitelskou aplikaci. Místo toho tato třída reprezentuje doplňku VSTO samotného a poskytuje členy, které můžete použít pro přístup k modelu objektu hostitelské aplikace a přistupovat k dalším funkcím, které jsou k dispozici pro doplňky VSTO. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Zahrnout všechny generované třídy v projektech pro systém Office `Startup` a `Shutdown` obslužných rutin událostí. Abyste mohli začít psát kód, obvykle přidejte kód do těchto obslužných rutin událostí. K inicializaci doplňku VSTO, můžete přidat kód, který `Startup` obslužné rutiny události. Pokud chcete vyčistit prostředky využívané třídou doplňku VSTO, můžete přidat kód, který `Shutdown` obslužné rutiny události. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="access-the-generated-classes-at-runtime"></a>Přístup k generované třídy za běhu  
 Při načítání řešení Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vytvoří instanci každý z vygenerovaných tříd ve vašem projektu. Tyto objekty lze přístup z jakéhokoli kódu ve vašem projektu s použitím `Globals` třídy. Například můžete použít `Globals` třídy pro volání kódu `ThisAddIn` třídy z obslužné rutiny události tlačítko pásu karet v doplňku VSTO.  
  
 Další informace najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="namespace-considerations-in-office-solutions"></a>Důležité informace o Namespace v řešeních pro systém Office  
 Nelze změnit *výchozí obor názvů* (nebo *kořenový obor názvů* v jazyce Visual Basic) Office Project po vytvoření projektu. Výchozí obor názvů se vždy odpovídat názvu projektu, který jste zadali při vytváření projektu. Pokud přejmenujete projekt, výchozí obor názvů se nezmění. Další informace o výchozí obor názvů v projektech, naleznete v tématu [stránka aplikace, Návrhář projektu &#40;C&#35; &#41; ](/visualstudio/ide/reference/application-page-project-designer-csharp) a [stránka aplikace, Návrhář projektu &#40;jazyka Visual Basic&#41; ](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Změna oboru názvů tříd položek hostitele v projektech C#  
 Hostování tříd položek (například `ThisAddIn`, `ThisWorkbook`, nebo `ThisDocument` třídy) mají své vlastní obory názvů v projektech Visual C# Office. Ve výchozím nastavení obor názvů pro hostitelské položky ve vašem projektu odpovídá názvu projektu, který jste zadali při vytváření projektu.  
  
 Chcete-li změnit obor názvů hostitelské položky v projektu Visual C# Office, použijte **Namespace pro hostitelský objekt** vlastnost. Další informace najdete v tématu [vlastnosti v projektech pro systém Office](../vsto/properties-in-office-projects.md).  
  
## <a name="supported-programming-languages-in-office-projects"></a>Podporované programovací jazyky v projektech pro systém Office  
 Šablony projektů pro Office v sadě Visual Studio podporují pouze jazyce Visual Basic a Visual C# programovacích jazyků. Proto nejsou k dispozici pouze v rámci těchto šablon projektů **jazyka Visual Basic** a **Visual C#** uzly **nový projekt** dialogové okno v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="language-choice-and-office-programming"></a>Volba jazyka a programování pro systém Office  
 Aplikace Microsoft Office a Visual Basic for Applications (VBA) byly vyvinuty spolupráce pro optimalizaci pracovního postupu přizpůsobení aplikace. Visual Basic zdědil některé z těchto vývoje. Například Visual Basic podporuje volitelné parametry, což znamená, že při volání některé metody v primární definiční sestavení Microsoft Office než při použití jazyka Visual C# můžete napsat menším množstvím kódu.  
  
## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Program s vs jazyka Visual Basic. Visual C# v řešeních pro systém Office  
 Řešení pro Office můžete vytvořit pomocí jazyka Visual Basic nebo Visual C#. Vzhledem k tomu, Microsoft Office – objektové modely byly navrženy pro použití s Microsoft Visual Basic for Applications (VBA), vývojáře jazyka Visual Basic můžete pohodlně pracovat s objekty vystavené aplikace Microsoft Office. Visual C# mohou vývojáři většinu stejné funkce jako vývojáři v jazyce Visual Basic, ale existují případy, kdy musíte napsat další kód, který použijete Office – objektové modely. Existují také některé rozdíly mezi základní funkce programování v vývoj pro Office a spravovaný kód napsaný v jazyce Visual Basic a C#.  
  
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Hlavní rozdíly mezi Visual Basic a Visual C#  
 Následující tabulka uvádí hlavní rozdíly mezi Visual Basic a Visual C# v vývoj pro Office.  
  
|Funkce|Popis|Podpora jazyka Visual Basic|Podpora Visual C#|  
|-------------|-----------------|--------------------------|------------------------|  
|Volitelné parametry|Mnoho metod Microsoft Office mají parametry, které nejsou nutné voláte metodu. Pokud není předána žádná hodnota pro parametr, je použita výchozí hodnota.|Visual Basic podporuje volitelné parametry.|Visual C# ve většině případů podporuje volitelné parametry. Další informace najdete v tématu [volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Předávání parametrů odkazem.|Volitelné parametry ve většině primární definiční sestavení Microsoft Office může být předán podle hodnoty. Některé primárních sestavení vzájemné spolupráce, musí být předána volitelné parametry, které přijímají typy odkazů podle odkazu.<br /><br /> Další informace o parametrech typu hodnoty a odkazu, naleznete v tématu [předávání argumentů podle hodnoty a podle reference &#40;jazyka Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (pro jazyk Visual Basic) a [předávat parametry &#40;C&#35; Průvodce programováním pro&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Žádné další kroky je potřeba pro předání parametrů podle odkazu. Parametry kompilátoru jazyka Visual Basic automaticky předá odkazem. Pokud je to nezbytné.|Ve většině případů kompilátor Visual C# automaticky předá parametry podle odkazu, pokud je to nezbytné. Další informace najdete v tématu [volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Parametrizované vlastnosti|Některé vlastnosti přijímají parametry a fungují jako funkce jen pro čtení.|Visual Basic podporuje vlastnosti, které přijímají parametry.|Visual C# podporuje vlastnosti, které přijímají parametry.|  
|Pozdní vazba|Pozdní vazby zahrnuje určení vlastnosti objektů za běhu, místo proměnných přetypování na typ objektu v době návrhu.|Visual Basic provádí pozdní vazby při **Option Strict** je vypnuté. Když **Option Strict** zapnutý, je nutné explicitně převést objekty a použití typů v <xref:System.Reflection> obor názvů pro přístup ke členům s pozdní vazbou. Další informace najdete v tématu [pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md).|Visual C# provádí pozdní vazby v projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Další informace najdete v tématu [pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md).|  
  
## <a name="key-differences-between-office-development-and-managed-code"></a>Hlavní rozdíly mezi vývoj pro Office a spravovaný kód  
 Následující tabulka uvádí hlavní rozdíly mezi vývoj pro Office a spravovaný kód napsaný v jazyce Visual Basic nebo Visual C#.  
  
|Funkce|Popis|Podpora jazyka Visual Basic a Visual C#|  
|-------------|-----------------|-----------------------------------------|  
|Indexy pole|Dolní mez pole z kolekce v aplikacích Microsoft Office začíná 1. Visual Basic a Visual C# pomocí pole založené na 0. Další informace najdete v tématu [pole &#40;C&#35; programováním&#41; ](/dotnet/csharp/programming-guide/arrays/index) a [pole v jazyce Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Pro přístup k první položku v kolekci v objektovém modelu aplikace Microsoft Office, použijte místo 0 index 1.|  
  
## <a name="see-also"></a>Viz také:  
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Události v projektech pro systém Office](../vsto/events-in-office-projects.md)   
 [Postupy: aplikace Office cílové primárních sestaveních vzájemné spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md)   
 [Spolupráce na vývoji řešení pro systém Office](../vsto/collaborative-development-of-office-solutions.md)  
  
  