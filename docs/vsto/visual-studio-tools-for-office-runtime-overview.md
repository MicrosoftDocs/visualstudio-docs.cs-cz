---
title: Visual Studio Tools for Office runtime – přehled
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b169242b9828f47f1ecfb87ebf02a9f86234699f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836993"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Visual Studio Tools for Office runtime – přehled
  Spouštění řešení, které jsou vytvořeny pomocí nástroje Microsoft Office developer tools v sadě Visual Studio, Visual Studio 2010 Tools for Office runtime musí nainstalovat na počítačích koncových uživatelů. Další informace najdete v tématu [postupy: instalace aplikace Visual Studio Tools for Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio 2010 Tools for Office runtime obsahuje dvě hlavní součásti:  
  
- Rozšíření Office pro rozhraní .NET Framework. Tyto součásti jsou spravovaná sestavení, která poskytují komunikační vrstvu mezi vaším řešením a aplikací Microsoft Office. Další informace najdete v tématu [vysvětlení rozšíření Office pro rozhraní .NET Framework](#officeextensions).  
  
- Zavaděč řešení pro Office. Tato součást je sada nespravovaných knihoven DLL, pomocí nichž aplikace Office zavádějí modul runtime a vaše řešení. Další informace najdete v tématu [pochopit zavaděče řešení Office](#UnmanagedLoader).  
  
  K dispozici je několik různých možností, jak nainstalovat modul runtime. V závislosti na konfiguraci počítače jsou při instalaci modulu runtime nainstalovány jeho různé součásti. Další informace najdete v tématu [Visual Studio Tools for Office runtime instalace scénáře](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
##  <a name="officeextensions"></a> Vysvětlení rozšíření Office pro rozhraní .NET Framework  
 Visual Studio 2010 Tools for Office runtime obsahuje rozšíření Office pro rozhraní .NET Framework 3.5 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a novější. Řešení, která cílí na jednotlivé verze rozhraní .NET Framework, používají příslušné rozšíření pro danou verzi.  
  
 Tato rozšíření jsou tvořena sestaveními, pomocí nichž mohou vaše řešení automatizovat a rozšířit aplikace Office. Když vytvoříte projekt pro Office, sada Visual Studio automaticky přidá odkazy na sestavení, která se používají pro zvolený typ projektu a cílové rozhraní .NET Framework projektu. Další informace o sestaveních v rozšířeních Office naleznete v tématu [sestavení ve Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
### <a name="design-differences-in-the-office-extensions"></a>Rozdíly v návrhu v rozšířeních sady Office  
 Většina typů, které můžete používat v rozšířeních Office pro .NET Framework 3.5, jsou třídy. Jedná se o stejné třídy, které byly obsaženy v předchozích verzích [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Naopak většina typů, které můžete používat v rozšířeních Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo jsou novější rozhraní. Například, pokud cílíte [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, <xref:Microsoft.Office.Tools.Excel.Worksheet> a <xref:Microsoft.Office.Tools.Word.Document> typy budou rozhraním namísto třídy.  
  
 Ve většině případů kód, který píšete v řešeních pro systém Office je stejný, ať vaše řešení cílí rozhraní .NET Framework 3.5 nebo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Při cílení na různé verze rozhraní .NET Framework ale některé funkce vyžadují odlišný kód. Další informace najdete v tématu [řešení pro systém Office migrovat na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Rozhraní v rozšířeních Office pro rozhraní .NET Framework 4 nebo novější  
 Většina rozhraní v rozšířeních Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později nejsou určeny k implementaci uživatelským kódem. Pouze rozhraní, které můžete implementovat přím, jejichž název začíná písmenem **můžu**, jako například <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.  
  
 Všechna rozhraní, které nezačínají písmenem **můžu** jsou implementována interně modulem Visual Studio 2010 Tools for Office runtime a tato rozhraní se mohou v budoucích verzích změnit. Chcete-li vytvořit objekty, které implementují tato rozhraní, použijte metody poskytované objektem `Globals.Factory` ve vašem projektu. Například, chcete-li získat objekt, který implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> rozhraní, použijte `Globals.Factory.CreateSmartTag` metody. Další informace o `Globals.Factory`, naleznete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Povolení rovnocennosti typů a vložených typů v projektech cílených rozhraní .NET Framework 4 nebo novější  
 Protože objektový model rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později jsou založené na rozhraních, můžete použít funkci rovnocennosti typů v jazyce Visual C# i Visual Basic v sadě Visual Studio pro vložení informací o typu ze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do vašeho řešení . Tato funkce umožňuje řešení pro systém Office a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pro verzování nezávisle na sobě navzájem. Například, pokud vaše řešení používá <xref:Microsoft.Office.Tools.Word.Document> rozhraní jako vložený typ a další verze modulu runtime přidá členy <xref:Microsoft.Office.Tools.Word.Document> rozhraní, vaše řešení stále fungovat s další verzí modulu runtime. Pokud vaše řešení nepoužívá <xref:Microsoft.Office.Tools.Word.Document> rozhraní jako vložený typ, pak vaše řešení přestane fungovat s další verzí modulu runtime.  
  
 Ve výchozím nastavení, není povolena funkce typu ekvivalence při vytváření projektu aplikace Office, který cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Pokud chcete tuto funkci povolit, nastavte **Embed Interop Types** vlastnost některého z následujících odkazů na sestavení v projektu na **True**:  
  
- Microsoft.Office.Tools.dll  
  
- Microsoft.Office.Tools.Common.dll  
  
- Microsoft.Office.Tools.Excel.dll  
  
- Microsoft.Office.Tools.Outlook.dll  
  
- Microsoft.Office.Tools.Word.dll  
  
  Když projekt po provedení této změny sestavíte, budou informace o typech pro všechny typy modulu runtime používané projektem vloženy do sestavení řešení. Tyto informace vložený typ, nikoli informací o typech v odkazovaných sestaveních jsou používány řešení za běhu.  
  
##  <a name="UnmanagedLoader"></a> Vysvětlení zavaděče řešení Office  
 Visual Studio Tools for Office runtime obsahuje několik nespravovaných knihoven DLL, které aplikacím Office se načíst modul runtime a řešení pro systém Office. I když by nikdy nemělo být nutné pracovat s těmito knihovnami DLL přímo, znalost účelu těchto knihoven DLL vám může pomoci lépe porozumět architektuře řešení pro Office.  
  
 Informace o tom, jak jsou tyto součásti používány během procesu načítání najdete v tématu [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md) a [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="vstoeedll"></a>VSTOEE.dll  
 Když uživatel otevře přizpůsobení na úrovni dokumentu nebo spustí doplněk VSTO, aplikace Office zavolá do *VSTOEE.dll* k provedení úloh potřebných k načtení [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 *VSTOEE.dll* zajišťuje, že správná verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] je načtena pro řešení a nainstalovanou verzi sady Office. Ačkoli více verzí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] může být nainstalovaný na stejném počítači, pouze jedna instance *VSTOEE.dll* je nainstalována. Toto je *VSTOEE.dll* , která je obsažena v nejnovější verzi modulu runtime nainstalovaného v počítači. Další informace o různých verzích [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , které můžete použít pro ostatní řešení, najdete v článku [spouštění řešení v různých verzích systému Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
### <a name="vstoloaderdll"></a>VSTOLoader.dll  
 Po *VSTOEE.dll* načte příslušnou verzi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], *knihovna VSTOLoader.dll* provede většinu práce, která je zapotřebí pro zavedení sestavení řešení. *Knihovna VSTOLoader.dll* provádí několik operací:  
  
- Vytvoří doménu aplikace pro každé sestavení řešení.  
  
- Pomocí kontrol zabezpečení ověří, zda má sestavení řešení oprávnění ke spuštění.  
  
- Načte verzi rozšíření Office pro rozhraní .NET Framework, které je požadováno řešením.  
  
  *Knihovna VSTOLoader.dll* také provádí několik operací, které jsou specifické pro doplňky VSTO:  
  
- Implementuje <xref:Extensibility.IDTExtensibility2> rozhraní. <xref:Extensibility.IDTExtensibility2> je rozhraní modelu COM, který musí implementovat všechny doplňků VSTO pro aplikace Microsoft Office. Toto rozhraní definuje metody, které aplikace volá při komunikaci s doplňku VSTO.  
  
- Imanagedaddin – rozhraní implementuje. Toto rozhraní se používá aplikace Office zavádějí doplňků VSTO. Další informace najdete v tématu [imanagedaddin – rozhraní](../vsto/imanagedaddin-interface.md).  
  
## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Vysvětlení 32bitové a 64bitové verze modulu runtime  
 Existují samostatné 64bitové a 32bitové verze sady Visual Studio 2010 Tools for Office runtime. Tyto verze modulu runtime se používají ke spouštění řešení v 64bitových a 32bitových edicích Office. Následující tabulka uvádí, která verze modulu runtime je vyžadována pro příslušnou kombinaci systému Windows a Office.  
  
|Edice systému Windows|Edice sady Microsoft Office|Požadovaná verze modulu Visual Studio Tools for Office Runtime|  
|------------------------|---------------------------------|--------------------------------------------------------------------|  
|32bitová|32bitová|32bitová|  
|64bitových|32bitová|64bitových|  
|64bitových|64bitových|64bitových|  
  
 Při instalaci sady Office, požadovaná verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] je spolu se sadou Office nainstalována. Například při instalaci 64bitové edice Office v 64bitové verzi systému Windows 64bitové verzi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] je rovněž nainstalován. Další informace o instalaci [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] se sadou Office, naleznete v tématu [Visual Studio Tools for Office runtime instalace scénáře](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 64bitová verze systému Office můžete také spustit řešení pro systém Office, které byly vytvořeny pomocí šablon projektů pro systém Microsoft Office 2007 v sadě Visual Studio 2008. Neumožňuje však spouštět řešení pro Office vytvořená pomocí šablon projektů pro Microsoft Office 2003 v sadě Visual Studio 2008 ani řešení pro Office vytvořená pomocí sady Visual Studio 2005. Další informace najdete v tématu [spouštění řešení v různých verzích systému Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Opravte Visual Studio 2010 Tools for Office runtime  
 Pokud potřebujete opravit modul runtime, otevřete **programy a funkce** nebo **přidat nebo odebrat programy** v Ovládacích panelech vyberte **Microsoft Visual Studio 2010 Tools for Office Runtime**v seznamu programy a klikněte na tlačítko **odinstalovat**. Instalační program, který se spustí, umožňuje modul runtime opravit. Vyberete-li **změnu**, nebude vám nabídnuta možnost opravy modulu runtime.  
  
## <a name="see-also"></a>Viz také:  
 [Visual Studio Tools for Office runtime instalace scénáře](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Sestavení v nástrojích Visual Studio Tools pro systém Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [Architektura řešení pro Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Upgrade a migrace řešení Office](../vsto/upgrading-and-migrating-office-solutions.md)  
  
  