---
title: Upgrade a migrace řešení Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b86699f11ab59aaf0ef09f5c7ae52d69e41e96c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671739"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Upgrade a migrace řešení Office
  Pokud máte projekt Microsoft Office, který byl vytvořen v dřívější verzi sady Visual Studio, musíte upgradovat projekt pro použití v aktuálních verzích sady Visual Studio. K upgradu aplikace Microsoft Office project, otevřete ho ve verzi Visual Studio, která zahrnuje nástroje Microsoft Office developer tools. Další informace o verzích sady Visual Studio, které zahrnují nástroje Microsoft Office developer tools, naleznete v tématu [konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
> [!NOTE]  
>  Visual Studio nemůže upgradovat projekty ze šablony formuláře InfoPath, které byly vytvořeny pomocí předchozí verze sady Visual Studio. Tyto typy projektů nejsou podporovány v aktuální verzi sady Visual Studio.  
  
## <a name="changes-to-upgraded-projects"></a>Změny upgradovaných projektů  
 Při upgradu aplikace Microsoft Office project Visual Studio změní projekt tak, aby cílil na následující položky:  
  
-   Visual Studio 2010 Tools for Office runtime. Další informace najdete v tématu [Visual Studio Tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Odkazy na aktuální sestavení.  
  
-   Verze rozhraní .NET Framework, která je podporována typem projektu (při upgradu na Visual Studio 2013 pouze).  
  
-   Verze systému Microsoft Office, která je podporována typem projektu (při upgradu na Visual Studio 2013 pouze).  
  
## <a name="assembly-references"></a>Odkazy na sestavení  
 Visual Studio upgraduje následující odkazy na sestavení v projektu:  
  
-   Aplikace Microsoft Office sestavení primární spolupráce (PIA).  
  
-   Sestavení v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Další informace o těchto sestaveních naleznete v tématu [Visual Studio Tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Nové nebo aktualizované verze závislých sestavení.  
  
## <a name="targeted-net-framework"></a>Cílové rozhraní .NET Framework  
 Při upgradu projektu sady Visual Studio 2013, Visual Studio změní projekt, aby cílil buď [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] nebo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Verze rozhraní .NET framework, který je cílem projektu závisí na verzi systému Office nainstalovaného v počítači. Pokud [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] je nainstalován, Visual Studio změní projekt, aby mířil [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. V opačném případě Visual Studio změní projekt, aby mířil [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Možná budete muset provést některé další kroky ke spuštění znovu cíleného řešení na vývoj a počítačích koncových uživatelů a projekt nebude již kompilován, pokud používá určité funkce. Další informace najdete v tématu [řešení pro systém Office migrovat na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Pokud cílíte [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později v projektu Office, můžete použít některé funkce, které nejsou k dispozici, pokud je cílem rozhraní .NET Framework 3.5. Další informace najdete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Cílová aplikace Office  
 Při upgradu aplikace Office project Visual Studio 2013, Visual Studio změní projekt na cílovou verzi sady Microsoft Office, která je podporována typem projektu, například přizpůsobení na úrovni dokumentu projektu nebo projektu doplňku VSTO.  
  
 Můžete cílit na projektech pro systém Office v sadě Visual Studio 2013 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikací. Visual Studio změní projekt cílit na nejnovější verzi office, kterou jste nainstalovali. Pokud nejsou nainstalované žádné z těchto verzí systému Office, Visual Studio upgrade projektu.  
  
> [!NOTE]  
>  Pokud upgradujete projekt doplňku VSTO k cíli [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] nebo novější, ujistěte se, že `ThisAddIn_Startup` obslužná rutina události doplňku VSTO neobsahuje kód, který přistupuje k dokumentu v aplikaci. Další informace najdete v tématu [přístup k dokumentu, při spuštění aplikace Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Přizpůsobení na úrovni dokumentu [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] převede dokumenty projektu, které mají binární formát, jako jsou například dokumenty, které mají *.xls* nebo *doc* rozšíření na formát Office Open XML. Další informace o Open XML naleznete v tématu [Úvod do nové přípony názvů souborů a Open XML formáty](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Inteligentní značky jsou zastaralé v aplikaci Excel 2010 a Word 2010. Proto pokud vaše řešení používá inteligentní značky, je nutné odebrat je bylo možné testovat a ladit v sadě Visual Studio 2013 nebo Visual Studio 2015.  
  
## <a name="upgrade-microsoft-office-2003-projects"></a>Upgrade projektů Microsoft Office 2003  
 Existují některé další důležité aspekty upgradu přizpůsobení na úrovni dokumentu a doplňků VSTO, které se zaměřují Microsoft Office 2003.  
  
### <a name="document-level-projects"></a>Projekty na úrovni dokumentu  
 Pokud dokument v projektu obsahuje ovládací prvky Windows Forms, musíte také mít Visual Studio 2005 Tools for Office Second Edition Runtime nainstalovat před upgradem projektu. Pokud tato verze modulu runtime není nainstalována na vývojovém počítači před upgradem projektu, upgradovaný projekt může obsahovat kompilace nebo chyby v době spuštění. Po dokončení upgradu projektu můžete odinstalovat Visual Studio 2005 Tools for Office Second Edition Runtime z vývojového počítače. Pokud není používán jinými řešeními sady Office. Tato verze modulu runtime je k dispozici jako redistribuovatelný balíček ze služby Microsoft Download Center na [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### <a name="vsto-add-in-projects"></a>Projekty doplňků VSTO  
 Pokud soubor řešení pro původní projekt obsahuje projekt instalace nebo InstallShield Limited Edition, který byl nakonfigurován k instalaci doplňku VSTO, Visual Studio upgradovat projekt, ale neprovede žádné další změny do projektu. Pokud chcete dál používat soubor Instalační služby systému Windows k nasazení vašeho doplňku VSTO, je nutné upravit projektu instalace nebo InstallShield Limited Edition pro instalaci nových prerekvizit jako [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools for Office Runtime a volitelně Primární spolupracující sestavení odkazuje doplňku VSTO. Další informace najdete v tématu [nasazení řešení Office s použitím Instalační služby systému Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Pokud chcete použít ClickOnce k nasazení vašeho doplňku VSTO, můžete zcela odstranit projekt instalace nebo InstallShield Limited Edition. Další informace o nasazení doplňků VSTO pomocí technologie ClickOnce, naleznete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: řešení pro systém Office upgradu](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)   
 [Migrace řešení Office na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Projekt upgradu, dialogové okno Možnosti](../vsto/project-upgrade-options-dialog-box.md)  
  
  