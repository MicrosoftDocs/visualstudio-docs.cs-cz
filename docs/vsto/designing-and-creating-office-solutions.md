---
title: Návrh a tvorba řešení pro systém Office
description: Přečtěte si, jak Visual Studio poskytuje šablony projektu, které můžete použít k vytvoření několika různých typů řešení pro systém Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df634a7c242819e4f41a6fddeae4099a3d25fae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897642"
---
# <a name="design-and-create-office-solutions"></a>Návrh a tvorba řešení pro systém Office

Sada Visual Studio poskytuje šablony projektu, které můžete použít k vytvoření několika různých typů řešení pro systém Office. Tato část dokumentace popisuje šablony projektů a poskytuje pokyny k vytváření projektů Office. Informace o tom, jak implementovat kód a přizpůsobení uživatelského rozhraní po vytvoření projektu, najdete v tématu [vývoj řešení pro Office](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Vytváření projektů pro Office
 Než začnete, měli byste určit své požadavky a zjistit typ řešení, které nabízí nejlepší přizpůsobení. Například pokud se vaše řešení Office musí spouštět při každém použití aplikace, doplněk VSTO vám nejlépe vyhovuje vašim požadavkům. Pokud je kód úzce integrovaný s jedním dokumentem, vytvořte přizpůsobení na úrovni dokumentu. Tyto typy projektů jsou k dispozici jako šablony projektů sady Visual Studio. Další informace o šablonách projektů Office, které jsou součástí sady Visual Studio, naleznete v tématu [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md). Další informace o tom, jak vytvořit projekty pro systém Office, naleznete v tématu [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Projekty Office mají funkce a položky projektu, které se liší od jiných typů projektů v sadě Visual Studio. Například při vytváření projektu na úrovni dokumentu může být dokument nebo sešit v projektu otevřen a upravován v rámci sady Visual Studio. Další informace najdete v tématu [projekty Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>Zvolit verzi .NET Framework
 Po výběru typu projektu, který nejlépe vyhovuje vašim požadavkům, můžete zvolit verzi .NET Framework, kterou chcete použít v procesu vývoje. V projektech Office můžete cílit na následující verze .NET Framework:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  Verze .NET Framework, kterou si zvolíte pro váš projekt, je požadována na počítačích koncových uživatelů, které mají vaše řešení běžet. Například pokud váš projekt cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] je vyžadován na počítačích koncových uživatelů. V tomto příkladu se řešení nespustí, pokud jsou na počítačích koncových uživatelů nainstalované jenom .NET Framework 3,5.

  Pokud migrujete projekt doplňku VSTO, který se zaměřuje na .NET Framework 3,5, Visual Studio změní cílové rozhraní projektu na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později v závislosti na verzi Office, kterou jste nainstalovali.

  Nicméně po změně cílového rozhraní sady Visual Studio může být nutné upravit kód v projektu, pokud používá určité funkce. Další informace o tom, jak změnit cílovou architekturu, naleznete v tématu [How to: Target a version of .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Další informace o změnách, které může být nutné provést v projektu, najdete v tématu [migrace řešení Office na .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

  Pokud aplikace Visual Studio změní cílovou .NET Framework pro váš projekt a používáte ClickOnce k nasazení vašeho řešení, ujistěte se, že jste v dialogovém okně **požadavky** vybrali také odpovídající verzi .NET Framework. Tento výběr se nemění automaticky při změně cílové architektury projektu. Další informace najdete v tématu [Postup: instalace požadovaných součástí na počítačích koncových uživatelů ke spouštění řešení pro Office](/previous-versions/bb608608(v=vs.110)).

> [!NOTE]
> V projektech pro systém Office, které vytvoříte pomocí, nelze cílit na .NET Framework 3,5 nebo starší [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] . Projekty Office, které vytvoříte pomocí nástroje [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , vyžadují funkce, které byly poprvé zavedeny do [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Informace o tom, kdy se na počítačích koncových uživatelů vyžaduje PIA Office
 Ve výchozím nastavení není nutné instalovat primární spolupracující sestavení (PIA) sady Office na počítačích koncových uživatelů, pokud je vlastnost **Embed Interop Types** každého odkazu PIA sady Office v projektu nastavena na **hodnotu true**, což je výchozí hodnota. V tomto scénáři jsou informace o typu pro typy PIA, které jsou používány řešením, vloženy do sestavení řešení při sestavení projektu. V době spuštění se místo PIA použije vložené informace o typu k volání do objektového modelu založeného na modelu COM aplikace Office. Další informace o tom, jak jsou typy z PIA vloženy do vašeho řešení, naleznete v tématu [ekvivalenci typu a vložené typy spolupráce](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Pokud je vlastnost **Embed Interop Types** každého odkazu PIA sady Office v projektu nastavena na **hodnotu false**, je nutné nainstalovat a zaregistrovat PIA sady Office v globální mezipaměti sestavení (GAC) na každém počítači koncového uživatele, který řešení spouští. Ve většině případů jsou PIA nainstalovány ve výchozím nastavení v systému Office, ale můžete také zahrnout distribuovatelné součásti PIA pro vaše řešení. Další informace najdete v tématu [předpoklady pro řešení pro systém Office pro nasazení](/previous-versions/bb608617(v=vs.110)).

### <a name="understand-the-client-profile"></a>Pochopení profilu klienta
 Profil klienta .NET Framework je podmnožinou úplné .NET Framework. Pokud potřebujete používat jenom klientské funkce v .NET Framework a chcete pro své řešení pro Office poskytnout nejrychlejší možné prostředí pro nasazení, můžete cílit na profil klienta .NET Framework. Další informace najdete v tématu [.NET Framework profil klienta](/dotnet/framework/deployment/client-profile).

 Při vytváření projektu Office, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] je výchozím cílem. Chcete-li vyvinout úplný vývoj, je [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nutné nastavit tuto možnost po vytvoření projektu. Další informace najdete v tématu [Postup: cílení na verzi .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Vytváření řešení pro 64 systém Microsoft Office edice
 Systém Microsoft Office je k dispozici v 64 a 32 bitových edicích. Chcete-li vytvořit řešení pro systém Office, která lze spustit v obou edicích, nastavení cíle platformy pro váš projekt musí být nastaveno na **Libovolný procesor**. Toto je výchozí hodnota pro projekty Office. Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

 K dispozici jsou samostatné 64 a 32 bitové verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , které jsou používány 64-bitovými 32 a 16bitovými edicemi systém Microsoft Office. Další informace najdete v tématu [Přehled modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Sestavení v řešeních pro systém Office
 Při vytváření projektu Office pomocí nástrojů pro vývoj pro Office v sadě Visual Studio se kód, který píšete, nakonec zkompiluje do sestavení. Sestavení je nasazeno na sdílený server nebo do adresáře v klientském počítači.

 Sestavení v řešeních pro systém Office jsou načítána aplikací Office. Po načtení sestavení může kód v sestavení reagovat na události, které jsou vyvolány v aplikaci, například když uživatel klikne na položku nabídky. Kód v sestavení může také volat objektový model pro automatizaci a rozšiřování aplikace a může použít libovolnou třídu v [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] . Další informace najdete v tématu [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md) a [architektury doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md).

 Řešení pro systém Office používají manifesty nasazení a manifesty aplikací k identifikaci sestavení. Manifesty obsahují informace o názvu, verzi a umístění sestavení, aby aplikace mohla najít, propojit a spustit správné sestavení. Další informace najdete v tématu [manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Projekty na úrovni dokumentu zahrnují kromě sestavení i dokument. Dokument funguje jako front-end aplikace a je tam, kde se koná veškerá interakce s uživatelem. Ke každému dokumentu může být přidruženo pouze jedno hlavní sestavení projektu; Nicméně více dokumentů může odkazovat na stejné sestavení.

 Sestavení v projektech na úrovni dokumentu nejsou vložena do dokumentu. místo toho jsou uloženy jinde a jsou identifikovány manifestem aplikace dokumentu.

## <a name="security-considerations-for-assemblies"></a>Požadavky na zabezpečení pro sestavení
 Aby bylo možné spustit řešení pro systém Office v počítači, musí být sestavení používaná řešením důvěryhodná pro spuštění. Další informace o zabezpečení najdete v tématu zabezpečení [řešení pro Office](../vsto/securing-office-solutions.md).

 Ve výchozím nastavení je sestavení řešení a všechna odkazovaná sestavení, která jsou v výstupní složce vašeho projektu, důvěryhodná pro spuštění ve vývojovém počítači při sestavování projektu. Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

 Z bezpečnostních důvodů je nejlepší vytvořit projekty na místním počítači místo vývoje ve sdíleném umístění. Další informace najdete v tématu [vývoj řešení pro Office ve spolupráci](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Odkazovaná sestavení
 Sestavení může odkazovat na jiná sestavení, která jsou uvedena v odkazech projektu. Některé sestavení projektu na úrovni dokumentu ale nemůže odkazovat na jiné sestavení projektu na úrovni dokumentu.

## <a name="see-also"></a>Viz také
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Projekty Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Vlastnosti v projektech pro systém Office](../vsto/properties-in-office-projects.md)
- [Spouštění řešení v různých verzích systém Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Postupy: nastavení informací o konfiguraci pro řešení pro systém Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Použití funkcí Office v sadě Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Běžné úlohy při programování pro systém Office](../vsto/common-tasks-in-office-programming.md)
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Architektura řešení pro systém Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)