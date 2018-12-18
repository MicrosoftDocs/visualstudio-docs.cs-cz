---
title: Návrh a vytvoření řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05cf317823d4f5853d960109bd97da77ea8a927d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671241"
---
# <a name="design-and-create-office-solutions"></a>Návrh a vytvoření řešení pro systém Office
  Visual Studio obsahuje šablony projektů, které můžete použít k vytvoření několika různých typů řešení pro systém Office. Tato část dokumentace popisuje šablony projektů a obsahuje pokyny k vytváření projektů Office. Informace o tom, jak implementovat kód a přizpůsobení uživatelského rozhraní, po vytvoření projektu naleznete v tématu [řešení pro vývoj Office](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
## <a name="create-office-projects"></a>Vytváření projektů Office  
 Než začnete, měli byste stanovit požadavky na a zjistit typ řešení, které nabízí nejvhodnější. Například, pokud vaše řešení pro Office musí spustit pokaždé, když se aplikace používá, doplňku VSTO nejlepší přizpůsobí vašim požadavkům. Pokud kód je úzce integrovaná s jednoho dokumentu, vytvoření přizpůsobení na úrovni dokumentu. Tyto typy projektů jsou k dispozici jako šablony projektů Visual Studio. Další informace o šablonách projektů Office, které jsou součástí sady Visual Studio najdete v tématu [Přehled šablon projektů Office project](../vsto/office-project-templates-overview.md). Další informace o tom, jak vytvářet projekty pro Office naleznete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Projekty Office mají funkcí a položek projektu, které se liší od ostatních typů projektů v sadě Visual Studio. Například při vytváření projektu úrovni dokumentu, dokumentu nebo sešitu ve vašem projektu může být otevřít a upravovat v sadě Visual Studio. Další informace najdete v tématu [projektech pro systém Office v prostředí sady Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="choose-a-net-framework-version"></a>Zvolte verzi rozhraní .NET Framework  
 Po výběru typu projektu, která nejlépe vyhovuje vašim požadavkům, můžete zvolit, kterou verzi rozhraní .NET Framework pro použití v procesu vývoje. Můžete cílit na následující verze rozhraní .NET Framework v projektech Office:  
  
- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
  Verze rozhraní .NET Framework, který jste vybrali pro váš projekt se vyžaduje v počítačích koncových uživatelů pro spuštění řešení. Například pokud váš projekt cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] se vyžaduje v počítačích koncových uživatelů. V tomto příkladu řešení nespustí, pokud pouze rozhraní .NET Framework 3.5 je nainstalovaný na počítačích koncových uživatelů.  
  
  Pokud provádíte migraci projektu doplňku VSTO, který cílí na rozhraní .NET Framework 3.5, sada Visual Studio změní cílovou architekturu projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novějším v závislosti na verzi Office, kterou jste nainstalovali.  
  
  Ale po sady Visual Studio změní cílovou architekturu, můžete potřebovat upravit kód ve vašem projektu, pokud používá určité funkce. Další informace o tom, jak změnit cílovou architekturu, naleznete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Další informace o změnách možná budete muset provést ve vašem projektu, naleznete v tématu [řešení pro systém Office migrovat na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
  Pokud Visual Studio změní cílového rozhraní .NET Framework pro váš projekt a jsou pomocí technologie ClickOnce k nasazení svého řešení, ujistěte se, že vyberete odpovídající verzi rozhraní .NET Framework v **požadavky** dialogové okno. Tento výběr nezmění automaticky, když změníte cílový rámec pro váš projekt. Další informace najdete v tématu [postupy: instalace požadovaných součástí v počítačích koncových uživatelů, které spouštějí řešení Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  Nelze cíleny na rozhraní.NET Framework 3.5 nebo starší v projektech Office, které vytvoříte pomocí [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. Projekty Office vytvořené pomocí [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] vyžadují funkce, které byly poprvé představeny v [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Seznamte se s při sestavení PIA sady Office jsou nutné v počítačích koncových uživatelů  
 Ve výchozím nastavení, Office sestavení primární spolupráce (PIA) nemusí být nainstalovaný na počítačích koncových uživatelů, pokud **Embed Interop Types** každého odkazu Office PIA v projektu je nastavena na **True**, což je výchozí hodnota. V tomto scénáři se vloží informace o typu pro typy PIA, které se používají ve vašem řešení do řešení sestavení při vytváření projektu. V době běhu informace o vloženém typu použít místo PIA pro volání do modelu COM založené na objektovém aplikace Office. Další informace o jak typy ze sestavení PIA jsou součástí vašeho řešení, najdete v části [ekvivalence typů a vestavěné typy spolupráce](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).  
  
 Pokud **Embed Interop Types** každého odkazu Office PIA v projektu je nastavena na **False**, sestavení PIA sady Office musí být nainstalovaný a zaregistrovaný v globální mezipaměti sestavení na každém počítači koncového uživatele, který spuštění řešení. Ve většině případů se PIA instalují ve výchozím nastavení se sadou Office, ale můžete také zahrnout PIA distribuovatelné jako požadavky vašeho řešení. Další informace najdete v tématu [požadavky řešení Office na nasazení](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="understand-the-client-profile"></a>Porozumět klientském profilu  
 Rozhraní .NET Framework Client Profile je podmnožinou úplné rozhraní .NET Framework. Můžete cílit rozhraní .NET Framework Client Profile, pokud je třeba použít pouze klientských funkcí v rozhraní .NET Framework a chcete poskytovat dispozici to nejrychlejší prostředí je to možné nasazení řešení Office. Další informace najdete v tématu [profil klienta rozhraní .NET Framework](/dotnet/framework/deployment/client-profile).  
  
 Při vytváření projektu aplikace Office, který cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] cílí ve výchozím nastavení. Pokud chcete vyvíjet pro kompletní [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], je nutné nastavit tuto možnost po vytvoření projektu. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Vytváření řešení pro 64bitová edice sady Microsoft Office  
 Aplikace Microsoft Office je k dispozici v 64bitových a 32bitových edicích. K vytvoření řešení pro systém Office, které lze spustit buď edition, nastavení cílové platformy pro váš projekt musí nastavit **jakýkoli procesor**. Toto je výchozí hodnota pro projekty pro Office. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
 Existují samostatné 64bitové a 32bitové verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , které jsou používány 64bitové a 32bitové verze systému Microsoft Office. Další informace najdete v tématu [Visual Studio Tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-office-solutions"></a>Sestavení v řešeních pro systém Office  
 Při vytváření projektu pro Office s použitím nástroje pro vývoj pro Office v sadě Visual Studio, který píšete kód nakonec zkompilovat do sestavení. Sestavení se nasadí na sdílený server nebo do adresáře v klientském počítači.  
  
 Sestavení v řešeních pro systém Office se načítají podle aplikace Office. Po sestavení je načteno, kód v sestavení můžou reagovat na události, které jsou vyvolány v aplikaci, například když uživatel klikne položku nabídky. Kód v sestavení můžete také volat do objektového modelu automatizovat a rozšířit aplikace, a můžou používat kterýkoli z třídy v [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Další informace najdete v tématu [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md) a [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).  
  
 Řešení pro systém Office pomocí manifesty aplikace a manifesty nasazení pro identifikaci sestavení. Manifesty obsahují informace o sestavení název, verzi a umístění, tak, aby aplikace můžete najít, propojení a spustit správné sestavení. Další informace najdete v tématu [aplikace a manifestů nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Zahrnout projekty na úrovni dokumentu dokument kromě sestavení. Dokument funguje jako front-endu aplikace a je, kde probíhá veškerou interakci uživatele. Každý dokument může mít pouze jedno sestavení hlavní projekt přidruženo; více dokumentů však může odkazovat na stejné sestavení.  
  
 Sestavení v projektech na úrovni dokumentu nejsou součástí dokumentu. Místo toho jsou uložená na jiném místě a jsou označeny identifikátorem dokumentu manifestu aplikace.  
  
## <a name="security-considerations-for-assemblies"></a>Informace o zabezpečení pro sestavení  
 Pro řešení Office spuštění na počítači musí být důvěryhodný pro spuštění sestavení, které používá řešení. Další informace o zabezpečení najdete v tématu [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).  
  
 Ve výchozím nastavení jsou důvěryhodné pro spuštění na vývojovém počítači při sestavování projektu sestavení řešení a jakákoli odkazovaná sestavení, které jsou ve výstupní složky vašeho projektu. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
 Z bezpečnostních důvodů je nejlepší vytvořit projekty do místního počítače, nikoli vývoj na sdílené umístění. Další informace najdete v tématu [spolupráce na vývoji řešení pro systém Office](../vsto/collaborative-development-of-office-solutions.md).  
  
## <a name="referenced-assemblies"></a>Odkazovaná sestavení  
 Sestavení lze odkazovat na jiná sestavení, které jsou uvedeny v odkazech projektu. Jedno sestavení projektu na úrovni dokumentu, ale nemůže odkazovat na jiné sestavení projektu na úrovni dokumentu.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Projekty pro Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Vlastnosti v projektech pro systém Office](../vsto/properties-in-office-projects.md)   
 [Spouštění řešení v různých verzích systému Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Postupy: aplikace Office cílové primárních sestaveních vzájemné spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Manifesty aplikace a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Postupy: nastavení informací o konfiguraci pro řešení Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Použití funkcí systému Office v sadě Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Běžné úlohy při programování pro systém Office](../vsto/common-tasks-in-office-programming.md)   
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Architektura řešení pro Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  