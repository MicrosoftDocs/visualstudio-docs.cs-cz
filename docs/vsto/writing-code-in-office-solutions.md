---
title: Psaní kódu v řešeních pro systém Office
description: Naučte se psát kód v systém Microsoft Office řešení a Naučte se, jakým způsobem jsou modely objektů Office vystaveny spravovanému kódu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b0f72e859e0847b5035e99146ef6c0435ef299d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904447"
---
# <a name="write-code-in-office-solutions"></a>Psaní kódu v řešeních pro systém Office
  Existují některé aspekty psaní kódu v projektech pro systém Office, které se liší od jiných typů projektů v sadě Visual Studio. Mnohé z těchto rozdílů se týkají způsobu, jakým jsou modely objektů Office vystaveny spravovanému kódu. Další rozdíly se týkají návrhu projektů Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Spravovaný kód a programování pro Office
 Klíčová technologie, která vytváří integrované řešení systém Microsoft Office, je automatizace, která je součástí technologie COM (Component Object Model). Automatizace umožňuje používat kód k vytváření a řízení softwarových objektů vystavených všemi aplikacemi, knihovnou DLL nebo ovládacím prvkem ActiveX, který podporuje odpovídající programová rozhraní.

### <a name="understand-primary-interop-assemblies"></a>Pochopení primárních sestavení vzájemné spolupráce
 Systém Microsoft Office aplikace zveřejňují většinu jejich funkcí pro automatizaci. Spravovaný kód (například Visual Basic nebo C#) ale nemůžete použít přímo k automatizaci aplikací Office. Chcete-li automatizovat aplikace Office pomocí spravovaného kódu, je nutné použít primární spolupracující sestavení (PIA) sady Office. Primární spolupracující sestavení umožňují spravovanému kódu pracovat s modelem objektu založeným na modelu COM aplikací Office.

 Každá aplikace systém Microsoft Office má hodnotu PIA. Při vytváření projektu Office v sadě Visual Studio se do projektu automaticky přidá odkaz na příslušné PIA. Chcete-li automatizovat funkce jiných aplikací Office z projektu, je nutné ručně přidat odkaz na příslušné PIA. Další informace naleznete v tématu [How to: Target Office Applications Through The Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Použít primární spolupracující sestavení v době návrhu a modulu runtime
 Abyste mohli provádět většinu vývojářských úloh, musíte mít nainstalovanou a zaregistrované PIA Office v globální mezipaměti sestavení (GAC) ve vývojovém počítači. Další informace najdete v tématu [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

 Na počítačích koncových uživatelů se nevyžadují PIA Office, aby bylo možné spouštět řešení Office, která cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Další informace najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="use-types-in-primary-interop-assemblies"></a>Použít typy v primárních sestaveních vzájemné spolupráce
 PIA Office obsahuje kombinaci typů, které zveřejňují objektový model aplikací Office a další typy infrastruktury, které nejsou určené pro použití přímo v kódu. Přehled typů v rámci PIA pro Office najdete v tématu [Přehled tříd a rozhraní v primárních sestaveních vzájemné spolupráce pro systém Office](/previous-versions/office/office-12/ms247299\(v\=office.12\)).

 Vzhledem k tomu, že typy v PIA Office odpovídají typům v modelech objektů založených na modelu COM, způsob, jakým tyto typy použijete, se často liší od jiných spravovaných typů. Například způsob volání metod, které mají volitelné parametry v primární definiční sestavení sady Office, závisí na programovacím jazyku, který používáte v projektu. Další informace najdete v následujících tématech:

- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md).

- [Pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md)

## <a name="program-model-of-office-projects"></a>Model programu projektů pro systém Office
 Všechny projekty Office obsahují jednu nebo více vygenerovaných tříd, které poskytují vstupní bod pro váš kód. Tyto třídy také poskytují přístup k objektovému modelu aplikace hostitele a přístup k funkcím, jako jsou podokna akcí a vlastní podokna úloh.

### <a name="understand-the-generated-classes"></a>Pochopení generovaných tříd
 V projektech na úrovni dokumentu v aplikaci Excel a Word se vygenerovaná třída podobá objektu nejvyšší úrovně v objektovém modelu aplikace. Například vygenerovaná `ThisDocument` Třída v projektu wordového dokumentu poskytuje stejné členy jako <xref:Microsoft.Office.Interop.Word.Document> Třída v objektovém modelu aplikace Word. Další informace o generovaných třídách v projektech na úrovni dokumentu najdete v tématu [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

 Projekty doplňku VSTO poskytují generovanou třídu s názvem `ThisAddIn` . Tato třída se nepodobá třídě v objektovém modelu hostitelské aplikace. Místo toho tato třída představuje samotný doplněk VSTO a poskytuje členy, které můžete použít pro přístup k objektovému modelu aplikace hostitele a k přístupu k dalším funkcím dostupným pro doplňky VSTO. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

 Všechny generované třídy v projektech systému Office zahrnují `Startup` a `Shutdown` obslužné rutiny událostí. Chcete-li začít psát kód, obvykle přidáte kód do těchto obslužných rutin událostí. K inicializaci doplňku VSTO můžete přidat kód do `Startup` obslužné rutiny události. K vyčištění prostředků používaných doplňkem VSTO můžete přidat kód do `Shutdown` obslužné rutiny události. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="access-the-generated-classes-at-run-time"></a>Přístup k vygenerovaným třídám v době běhu
 Po načtení řešení pro sadu Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vytvoří instance každého generované třídy v projektu. K těmto objektům můžete přistupovat z libovolného kódu v projektu pomocí `Globals` třídy. Můžete například použít `Globals` třídu pro volání kódu ve `ThisAddIn` třídě z obslužné rutiny události tlačítka pásu karet v doplňku VSTO.

 Další informace najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="namespace-considerations-in-office-solutions"></a>Hlediska oboru názvů v řešeních pro systém Office
 Po vytvoření projektu nelze změnit *výchozí obor názvů* (nebo *kořenový obor názvů* v Visual Basic) projektu Office. Výchozí obor názvů se vždycky bude shodovat s názvem projektu, který jste zadali při vytváření projektu. Pokud přejmenujete projekt, výchozí obor názvů se nemění. Další informace o výchozím oboru názvů v projektech najdete v tématu [Stránka aplikace, Návrhář projektu &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) a [Stránka aplikace, návrhář projektu &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md).

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Změna oboru názvů tříd hostitelských položek v projektech C#
 Třídy hostitelských položek (například `ThisAddIn` `ThisWorkbook` třídy, nebo `ThisDocument` ) mají své vlastní obory názvů v projektech Visual C# pro Office. Ve výchozím nastavení se obor názvů pro položky hostitele v projektu shoduje s názvem projektu, který jste zadali při vytváření projektu.

 Chcete-li změnit obor názvů hostitelských položek v projektu Visual C# Office, použijte **obor názvů pro vlastnost Item hostitele** . Další informace najdete v tématu [vlastnosti v projektech Office](../vsto/properties-in-office-projects.md).

## <a name="supported-programming-languages-in-office-projects"></a>Podporované programovací jazyky v projektech pro systém Office
 Šablony projektů Office v sadě Visual Studio podporují pouze programovací jazyky Visual Basic a Visual C#. Proto jsou tyto šablony projektů k dispozici pouze v uzlech **Visual Basic** a **Visual C#** dialogového okna **Nový projekt** v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="language-choice-and-office-programming"></a>Volba jazyka a programování pro Office
 Systém Microsoft Office a jazyk Visual Basic for Application (VBA) byly vyvinuty pro spolupráci k optimalizaci pracovního postupu přizpůsobení aplikace. Visual Basic zdědil některé z těchto vývojů. Například Visual Basic podporuje volitelné parametry, což znamená, že můžete napsat méně kódu při volání některých metod v systém Microsoft Office primárních spolupracujících sestaveních, než při použití jazyka Visual C#.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Program s Visual Basic vs. Visual C# v řešeních pro systém Office
 Můžete vytvářet řešení pro Office pomocí Visual Basic nebo Visual C#. Vzhledem k tomu, že systém Microsoft Office objektové modely byly navrženy pro použití s Microsoft jazyk Visual Basic for Application (VBA), vývojáři Visual Basic mohou pohodlně pracovat s objekty, které jsou vystaveny systém Microsoft Office aplikacemi. Vývojáři Visual C# můžou používat většinu stejných funkcí jako Visual Basic vývojářům, ale v některých případech musí napsat další kód pro použití objektových modelů Office. Mezi základními programovacími funkcemi ve vývoji pro Office a spravovaným kódem napsaným v Visual Basic a C# jsou také rozdíly.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Klíčové rozdíly mezi Visual Basic a Visual C #
<!-- markdownlint-enable MD003 MD020 -->

V následující tabulce jsou uvedeny klíčové rozdíly mezi Visual Basic a Visual C# při vývoji pro Office.

|Funkce|Popis|Podpora Visual Basic|Podpora Visual C#|
|-------------|-----------------|--------------------------|------------------------|
|Volitelné parametry|Mnoho metod systém Microsoft Office má parametry, které nejsou požadovány při volání metody. Pokud pro parametr není předána žádná hodnota, použije se výchozí hodnota.|Visual Basic podporuje volitelné parametry.|Ve většině případů podporuje Visual C# volitelné parametry. Další informace najdete v tématu [volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md).|
|Předávání parametrů odkazem|Volitelné parametry ve většině systém Microsoft Officech primárních sestavení vzájemné spolupráce mohou být předány hodnotou. V některých primárních sestaveních spolupráce však musí být nepovinné parametry, které přijímají odkazové typy, předány odkazem.<br /><br /> Další informace o parametrech typu hodnoty a odkazu naleznete v tématu [Pass argumentů podle hodnoty a odkaz &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (pro Visual Basic) a [Pass parameters &#40;C&#35; program průvodce programováním&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|K předání parametrů odkazem se nevyžaduje žádná další práce. Kompilátor Visual Basic v případě potřeby automaticky předává parametry podle odkazu.|Ve většině případů kompilátor Visual C# automaticky předává parametry podle odkazu v případě potřeby. Další informace najdete v tématu [volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md).|
|Parametrizované vlastnosti|Některé vlastnosti přijímají parametry a fungují jako funkce jen pro čtení.|Visual Basic podporuje vlastnosti, které přijímají parametry.|Visual C# podporuje vlastnosti, které přijímají parametry.|
|Pozdní vazba|Pozdní vazba zahrnuje určení vlastností objektů za běhu, namísto přetypování proměnných na typ objektu v době návrhu.|Visual Basic provádí pozdní vazbu, je-li **možnost Option Strict** vypnutá. Pokud je **parametr Option Strict** zapnutý, je nutné explicitně převést objekty a použít typy v <xref:System.Reflection> oboru názvů pro přístup ke členům s pozdní vazbou. Další informace najdete v tématu [pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md).|Visual C# provede pozdní vazbu v projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Další informace najdete v tématu [pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md).|

## <a name="key-differences-between-office-development-and-managed-code"></a>Klíčové rozdíly mezi vývojem a spravovaným kódem pro Office
 V následující tabulce jsou uvedeny klíčové rozdíly mezi vývojem a spravovaným kódem Office napsaným v Visual Basic nebo v jazyce Visual C#.

|Funkce|Popis|Podpora Visual Basic a Visual C#|
|-------------|-----------------|-----------------------------------------|
|Indexy polí|Dolní hranice pole kolekcí ve systém Microsoft Officech aplikacích začíná 1. Visual Basic a Visual C# používají pole na 0. Další informace najdete v tématu [pole &#40;C&#35; Průvodce programováním&#41;](/dotnet/csharp/programming-guide/arrays/index) a [pole v Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Chcete-li získat přístup k první položce kolekce v objektovém modelu aplikace systém Microsoft Office, použijte index 1 místo 0.|

## <a name="see-also"></a>Viz také

- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Události v projektech pro systém Office](../vsto/events-in-office-projects.md)
- [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md)
- [Spolupráce na vývoji řešení pro systém Office](../vsto/collaborative-development-of-office-solutions.md)
