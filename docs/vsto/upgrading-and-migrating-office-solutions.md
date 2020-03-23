---
title: Upgrade a migrace řešení Office
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e421d6e4ee94d9974c0a0583db1fb495c72593e
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416533"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Upgrade a migrace řešení Office
  Pokud máte projekt sady Microsoft Office, který byl vytvořen v dřívější verzi sady Visual Studio, je nutné upgradovat projekt tak, aby jej používal v aktuálních verzích sady Visual Studio. Chcete-li upgradovat projekt sady Microsoft Office, otevřete jej ve verzi sady Visual Studio, která obsahuje vývojářské nástroje sady Microsoft Office. Další informace o verzích sady Visual Studio, které obsahují vývojářské nástroje sady Microsoft Office, naleznete v [tématu Konfigurace počítače pro vývoj řešení sady Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio nemůže upgradovat projekty šablon formulářů aplikace InfoPath, které byly vytvořeny pomocí předchozích verzí sady Visual Studio. Tyto typy projektů nejsou podporovány v aktuální verzi sady Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Změny upgradovaných projektů
 Při upgradu projektu sady Microsoft Office visual studio upraví projekt tak, aby cílil na následující položky:

- Visual Studio 2010 Tools for Office runtime. Další informace naleznete v [tématu Visual Studio Tools for Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Aktuální odkazy na sestavení.

- Verze rozhraní .NET Framework, která je podporována typem projektu (Při upgradu pouze na Visual Studio 2013).

- Verze Microsoft Office, která je podporovaná typem projektu (Při upgradu pouze na Visual Studio 2013).

## <a name="assembly-references"></a>Odkazy na sestavení
 Visual Studio upgraduje následující odkazy na sestavení v projektu:

- Primární sestavení mezi opačkami sady Sady Microsoft Office (PIA).

- Sestavení v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Další informace o těchto sestaveních naleznete v [tématu Visual Studio Tools for Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Nové nebo aktualizované verze závislých sestavení.

## <a name="targeted-net-framework"></a>Cílená architektura .NET
 Při upgradu projektu na Visual Studio 2013 Visual Studio upraví [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] projekt [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]na cíl nebo . Verze rozhraní .NET, na které se projekt zaměřuje, závisí na tom, jaká verze sady Office je v počítači nainstalovaná. Pokud [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] je nainstalován, Visual Studio upraví projekt [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]na cíl . V opačném případě Visual Studio upraví [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]projekt na cíl .

> [!NOTE]
> Možná budete muset provést některé další kroky ke spuštění retargeted řešení na vývoj a počítače koncových uživatelů a váš projekt již nebude kompilovat, pokud používá určité funkce. Další informace naleznete [v tématu Migrace řešení sady Office do rozhraní .NET Framework 4 nebo novější .](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)

 Pokud cílíte [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější v projektu sady Office, můžete použít některé funkce, které nejsou k dispozici, když cílíte na rozhraní .NET Framework 3.5. Další informace naleznete v [tématu Návrh a vytvoření řešení Sady Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Cílená aplikace Office
 Při upgradu projektu Office na Visual Studio 2013 visual studio upraví projekt tak, aby se zaměřil na verzi sady Microsoft Office, která je podporována typem projektu, jako je například projekt přizpůsobení na úrovni dokumentu nebo projekt doplňku VSTO.

 Projekty Office v Sadě Visual [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] Studio [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 2013 můžou cílit a aplikace. Visual Studio upraví projekt tak, aby se zaměřil na nejnovější verzi sady Office, kterou jste nainstalovali. Pokud není nainstalována žádná z těchto verzí sady Office, visual studio neupgraduje projekt.

> [!NOTE]
> Pokud inovujete projekt doplňku VSTO na cíl [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] `ThisAddIn_Startup` nebo novější, ujistěte se, že obslužná rutina události doplňku VSTO neobsahuje kód, který přistupuje k dokumentu v aplikaci. Další informace naleznete [v tématu Access a document when the Office application starts](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Pro vlastní nastavení na [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] úrovni dokumentu převede dokumenty v projektu, které mají binární formát, například dokumenty, které mají *příponu XLS* nebo *.doc,* do formátu Office Open XML. Další informace o open xml naleznete [v tématu Úvod do nových přípon názvů souborů a formátů Open XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Inteligentní značky se v Excelu 2010 a Wordu 2010 zastaraly. Proto pokud vaše řešení používá inteligentní značky, je nutné je odebrat před testováním a laděním v sadě Visual Studio 2013 nebo Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Upgrade projektů sady Microsoft Office 2003
 Existují některé další důležité informace pro upgrade vlastního nastavení na úrovni dokumentu a doplňků VSTO, které cílí na sadu Microsoft Office 2003.

### <a name="document-level-projects"></a>Projekty na úrovni dokumentu
 Pokud dokument v projektu obsahuje ovládací prvky windows forms, musíte mít před upgradem projektu nainstalovány také nástroje visual studio 2005 Tools for Office Druhé vydání. Pokud tato verze runtime není nainstalována ve vývojovém počítači před upgradem projektu, upgradovaný projekt může obsahovat chyby kompilace nebo běhu. Po dokončení inovace projektu můžete odinstalovat nástroj Visual Studio 2005 Tools for Office Druhé vydání runtime z vývojového počítače, pokud jej nepoužívá jiná řešení sady Office. Tato verze runtime je k dispozici jako redistribuovatelný balíček ze služby Stažení softwaru společnosti Microsoft v [aplikaci Microsoft Visual Studio 2005 Tools for Office Druhé vydání runtime (VSTO 2005 SE) (x86).](https://www.microsoft.com/download/details.aspx?id=2392)

### <a name="vsto-add-in-projects"></a>VSTO Doplňkové projekty
 Pokud soubor řešení pro původní projekt zahrnoval projekt instalace nebo limitované edice InstallShield, který byl nakonfigurován pro instalaci doplňku VSTO, aplikace Visual Studio projekt upgraduje, ale neprovede žádné další změny v projektu. Chcete-li k nasazení doplňku VSTO nadále používat soubor Instalační služby systému Windows, je nutné upravit projekt Instalace [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]nebo limitované edice InstallShield a nainstalovat nové požadavky, jako jsou nástroje sady Visual Studio 2010 pro prostředí Office Runtime a volitelně primární meziop sestavení odkazovaná doplňkem VSTO. Další informace naleznete [v tématu Deploy an Office solution using Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 Pokud chcete použít ClickOnce k nasazení doplňku VSTO, můžete zcela odstranit projekt Instalační program nebo Limitovaná edice InstallShield. Další informace o nasazení doplňků VSTO pomocí ClickOnce naleznete v [tématu Deploy a Office solution](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také
- [Postup: Upgrade řešení Office](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Migrace řešení Office do rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Dialogové okno Upgrade projektu, možnosti](../vsto/project-upgrade-options-dialog-box.md)
