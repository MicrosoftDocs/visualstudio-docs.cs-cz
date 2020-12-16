---
title: Přehled prostředí Visual Studio Tools for Office runtime
description: Nástroje Visual Studio 2010 Tools for Office runtime musí být nainstalované na počítačích koncových uživatelů, aby mohli spouštět řešení vytvořená pomocí nástrojů systém Microsoft Office Developer Tools.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16431a9ba2fe56b88f9f6b7f2c874c75bfad61c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526272"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Přehled prostředí Visual Studio Tools for Office runtime
  Chcete-li spustit řešení vytvořená pomocí nástrojů systém Microsoft Office Developer Tools v sadě Visual Studio, je třeba nainstalovat nástroje Visual Studio 2010 Tools for Office runtime do počítačů koncových uživatelů. Další informace naleznete v tématu [How to: Install the Visual Studio Tools for Office Runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Sada Visual Studio 2010 Tools for Office runtime se skládá ze dvou hlavních součástí:

- Rozšíření Office pro rozhraní .NET Framework. Tyto součásti jsou spravovaná sestavení, která poskytují komunikační vrstvu mezi vaším řešením a aplikací Microsoft Office. Další informace najdete v tématu [vysvětlení rozšíření Office pro .NET Framework](#officeextensions).

- Zavaděč řešení pro Office. Tato součást je sada nespravovaných knihoven DLL, pomocí nichž aplikace Office zavádějí modul runtime a vaše řešení. Další informace najdete v tématu [vysvětlení zavaděče řešení pro Office](#UnmanagedLoader).

  K dispozici je několik různých možností, jak nainstalovat modul runtime. V závislosti na konfiguraci počítače jsou při instalaci modulu runtime nainstalovány jeho různé součásti. Další informace najdete v tématu [scénáře instalace modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

## <a name="understand-the-office-extensions-for-the-net-framework"></a><a name="officeextensions"></a> Pochopení rozšíření Office pro .NET Framework
 Sady Visual Studio 2010 Tools for Office runtime obsahují rozšíření Office pro .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a novější. Řešení, která cílí na jednotlivé verze rozhraní .NET Framework, používají příslušné rozšíření pro danou verzi.

 Tato rozšíření jsou tvořena sestaveními, pomocí nichž mohou vaše řešení automatizovat a rozšířit aplikace Office. Když vytvoříte projekt pro Office, sada Visual Studio automaticky přidá odkazy na sestavení, která se používají pro zvolený typ projektu a cílové rozhraní .NET Framework projektu. Další informace o sestaveních v rozšířeních sady Office naleznete v tématu [Assemblies in Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

### <a name="design-differences-in-the-office-extensions"></a>Rozdíly v návrhu v rozšířeních Office
 Většina typů, které můžete používat v rozšířeních Office pro .NET Framework 3.5, jsou třídy. Jedná se o stejné třídy, které byly součástí předchozích verzí nástroje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Naopak většina typů, které používáte v rozšířeních Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novějších, jsou rozhraní. Například když cílíte na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> typy a jsou rozhraním namísto tříd.

 Ve většině případů kód, který zapisujete do řešení pro systém Office, je stejný, bez ohledu na to, jestli vaše řešení cílí na .NET Framework 3,5 nebo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Při cílení na různé verze rozhraní .NET Framework ale některé funkce vyžadují odlišný kód. Další informace najdete v tématu [migrace řešení pro systém Office do .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Rozhraní v rozšířeních Office pro .NET Framework 4 nebo novější
 Většina rozhraní v rozšířeních sady Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novějších není určena k implementaci pomocí uživatelského kódu. Jediná rozhraní, která můžete implementovat přímo, mají názvy začínající písmenem **I**, například <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension> .

 Všechna rozhraní, která nezačínají písmenem **I** , jsou implementována interně nástroji Visual Studio 2010 Tools for Office runtime a tato rozhraní se mohou v budoucích verzích změnit. Chcete-li vytvořit objekty, které implementují tato rozhraní, použijte metody poskytované `Globals.Factory` objektem v projektu. Například chcete-li získat objekt, který implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> rozhraní, použijte `Globals.Factory.CreateSmartTag` metodu. Další informace o najdete v `Globals.Factory` tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Povolit ekvivalenci typů a vložené typy v projektech, které cílí na .NET Framework 4 nebo novější
 Vzhledem k tomu, že objektový model rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější je založen na rozhraních, můžete použít funkci rovnocennosti typů v jazyce Visual C# i Visual Basic v sadě Visual Studio pro vložení informací o typu z do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vašeho řešení. Tato funkce umožňuje, aby řešení Office a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verze byly nezávisle na sobě. Například pokud vaše řešení používá <xref:Microsoft.Office.Tools.Word.Document> rozhraní jako vložený typ a další verze modulu runtime přidává členy do <xref:Microsoft.Office.Tools.Word.Document> rozhraní, vaše řešení bude i nadále fungovat s další verzí modulu runtime. Pokud vaše řešení nepoužívá <xref:Microsoft.Office.Tools.Word.Document> rozhraní jako vložený typ, pak vaše řešení nebude nadále fungovat s další verzí modulu runtime.

 Ve výchozím nastavení není při vytváření projektu Office, který cílí na nebo novější, povolena funkce rovnocennosti typů [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Chcete-li povolit tuto funkci, nastavte vlastnost **Embed Interop Types** každého z následujících odkazů na sestavení v projektu na **hodnotu true**:

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  Když projekt po provedení této změny sestavíte, budou informace o typech pro všechny typy modulu runtime používané projektem vloženy do sestavení řešení. Tyto informace vloženého typu, nikoli informace o typu v odkazovaných sestaveních, jsou používány v rámci řešení v době běhu.

## <a name="understand-the-office-solution-loader"></a><a name="UnmanagedLoader"></a> Pochopení zavaděče řešení pro Office
 Modul runtime Visual Studio Tools for Office obsahuje několik nespravovaných knihoven DLL, které aplikace Office používají k načtení řešení runtime a sady Office. I když by nikdy nemělo být nutné pracovat s těmito knihovnami DLL přímo, znalost účelu těchto knihoven DLL vám může pomoci lépe porozumět architektuře řešení pro Office.

 Informace o tom, jak se tyto komponenty používají během procesu načítání, najdete v tématu [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md) a [architektury doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="vstoeedll"></a>VSTOEE.dll
 Když uživatel otevře přizpůsobení na úrovni dokumentu nebo spustí doplněk VSTO, aplikace Office zavolá do *VSTOEE.dll* a provede úkoly potřebné k načtení [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 *VSTOEE.dll* zajistěte, aby [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] se načetla správná verze pro řešení a nainstalovaná verze Office. I když [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] v jednom počítači může být nainstalováno více verzí nástroje, vždy je nainstalována pouze jedna instance *VSTOEE.dll* . Toto je *VSTOEE.dll* , která byla součástí nejnovější verze modulu runtime nainstalovaného v počítači. Další informace o různých verzích nástroje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , které lze použít pro jiná řešení, najdete v tématu [spuštění řešení v různých verzích systém Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 Poté, co *VSTOEE.dll* načte správnou verzi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , *VSTOLoader.dll* provádí většinu práce, která je požadována pro načtení sestavení řešení. *VSTOLoader.dll* několik věcí:

- Vytvoří doménu aplikace pro každé sestavení řešení.

- Pomocí kontrol zabezpečení ověří, zda má sestavení řešení oprávnění ke spuštění.

- Načte verzi rozšíření Office pro rozhraní .NET Framework, které je požadováno řešením.

  *VSTOLoader.dll* také několik věcí, které jsou specifické pro doplňky VSTO:

- Implementuje <xref:Extensibility.IDTExtensibility2> rozhraní. <xref:Extensibility.IDTExtensibility2> je rozhraní modelu COM, které musí implementovat všechny doplňky VSTO pro aplikace systém Microsoft Office. Toto rozhraní definuje metody, které aplikace volá ke komunikaci s doplňkem VSTO.

- Implementuje rozhraní IManagedAddin –. Toto rozhraní se používá v aplikacích Office, které vám pomůžou načíst doplňky VSTO. Další informace najdete v tématu [rozhraní IManagedAddin –](../vsto/imanagedaddin-interface.md).

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Principy 32 a 64 bitových verzí modulu runtime
 Existují samostatné 64 a 32 bitové verze nástroje Visual Studio 2010 Tools for Office runtime. Tyto verze modulu runtime se používají ke spouštění řešení v systémech 64 a 32-bit Edition. Následující tabulka uvádí, která verze modulu runtime je vyžadována pro každou kombinaci systémů Windows a Office.

|Edice systému Windows|Edice sady Microsoft Office|Požadovaná verze modulu Visual Studio Tools for Office Runtime|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32bitová|32bitová|32bitová|
|64bitová|32bitová|64bitová|
|64bitová|64bitová|64bitová|

 Při instalaci Office je požadovaná verze nástroje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nainstalovaná společně se sadou Office. Pokud například nainstalujete 64-bit edice sady Office na 64 verzi systému Windows, nainstalují se také verze 64-bit [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Další informace o instalaci nástroje v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sadě Office najdete v tématu [scénáře instalace modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 64 verze Office může také spouštět řešení pro Office, která byla vytvořena pomocí šablon projektů pro 2007 systém Microsoft Office systém v sadě Visual Studio 2008. Neumožňuje však spouštět řešení pro Office vytvořená pomocí šablon projektů pro Microsoft Office 2003 v sadě Visual Studio 2008 ani řešení pro Office vytvořená pomocí sady Visual Studio 2005. Další informace najdete v tématu [spuštění řešení v různých verzích systém Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Opravte Visual Studio 2010 Tools for Office runtime.
 Pokud potřebujete opravit modul runtime, otevřete ovládací panely **programy a funkce** nebo **Přidat nebo odebrat programy** , v seznamu programů vyberte **Microsoft Visual Studio 2010 Tools for Office runtime** a pak klikněte na **odinstalovat**. Instalační program, který se spustí, umožňuje modul runtime opravit. Pokud kliknete na **změnit**, nebudete mít možnost opravit modul runtime.

## <a name="see-also"></a>Viz také
- [Scénáře instalace Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Sestavení v modulu runtime Visual Studio Tools for Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Architektura řešení pro systém Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Upgrade a migrace řešení pro systém Office](../vsto/upgrading-and-migrating-office-solutions.md)
