---
title: Upgrade a migrace řešení pro systém Office
description: Pokud máte projekt Offince, který byl vytvořen v dřívější verzi sady Visual Studio, je třeba upgradovat projekt na jeho použití v aktuálních verzích sady Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b18b61ad6854be654582fe8a8a76da185ec9d89e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526610"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Upgrade a migrace řešení pro systém Office
  Pokud máte projekt systém Microsoft Office, který byl vytvořen v dřívější verzi sady Visual Studio, je nutné upgradovat projekt, aby jej bylo možné použít v aktuálních verzích sady Visual Studio. Chcete-li upgradovat projekt systém Microsoft Office, otevřete ho ve verzi sady Visual Studio, která obsahuje nástroje systém Microsoft Office Developer Tools. Další informace o verzích sady Visual Studio, které obsahují nástroje systém Microsoft Office Developer Tools, najdete v tématu [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio nemůže upgradovat projekty šablon formulářů aplikace InfoPath, které byly vytvořeny pomocí předchozích verzí sady Visual Studio. Tyto typy projektů nejsou v aktuální verzi sady Visual Studio podporovány.

## <a name="changes-to-upgraded-projects"></a>Změny upgradovaných projektů
 Při upgradu systém Microsoft Officeho projektu aplikace Visual Studio změní projekt tak, aby cílí na následující položky:

- Sady Visual Studio 2010 Tools for Office runtime. Další informace najdete v tématu [Přehled modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Odkazy na aktuální sestavení.

- Verze .NET Framework, která je podporována typem projektu (při upgradu na Visual Studio 2013).

- Verze systém Microsoft Office podporovaná typem projektu (při upgradu na Visual Studio 2013).

## <a name="assembly-references"></a>Odkazy na sestavení
 Visual Studio upgraduje následující odkazy na sestavení v projektu:

- Systém Microsoft Office primární spolupracující sestavení (PIA).

- Sestavení v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Další informace o těchto sestaveních naleznete v tématu [Visual Studio Tools for Office runtime – přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Nové nebo aktualizované verze závislých sestavení.

## <a name="targeted-net-framework"></a>Cílené .NET Framework
 Když upgradujete projekt na Visual Studio 2013, Visual Studio změní projekt tak, aby byl cílen na [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] nebo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Verze rozhraní .NET Framework, na kterou projekt cílí, závisí na tom, jaká verze sady Office je nainstalována v počítači. Pokud [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] je nainstalován, aplikace Visual Studio změní projekt tak, aby jeho cílem bylo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . V opačném případě Visual Studio změní projekt na cíl [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

> [!NOTE]
> Je možné, že budete muset provést některé další kroky, abyste mohli spustit přecílené řešení na počítačích s vývojem a koncovými uživateli a projekt už nebude zkompilován, pokud používá určité funkce. Další informace najdete v tématu [migrace řešení pro systém Office do .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 Pokud cílíte na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později v projektu Office, můžete použít některé funkce, které nejsou k dispozici, když cílíte na .NET Framework 3,5. Další informace najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Cílová aplikace Office
 Když upgradujete projekt Office na Visual Studio 2013, Visual Studio změní projekt tak, aby cílí na verzi systém Microsoft Office, která je podporována typem projektu, jako je například projekt přizpůsobení na úrovni dokumentu nebo projekt doplňku VSTO.

 Projekty Office v Visual Studio 2013 mohou cílit [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikace. Visual Studio změní projekt tak, aby se zacílely na nejnovější verzi Office, kterou jste nainstalovali. Pokud není nainstalována žádná z těchto verzí systému Office, sada Visual Studio projekt neupgraduje.

> [!NOTE]
> Pokud provedete upgrade projektu doplňku VSTO na cíl [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] nebo novější, ujistěte se, že `ThisAddIn_Startup` obslužná rutina události doplňku VSTO neobsahuje kód, který přistupuje k dokumentu v aplikaci. Další informace najdete v tématu [přístup k dokumentu při spuštění aplikace Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 V případě přizpůsobení na úrovni dokumentu [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] Převádí dokumenty v projektu, které mají binární formát, jako jsou například dokumenty s příponou *. xls* nebo *. doc* , do formátu Office Open XML. Další informace o Open XML najdete v tématu [Úvod do nových přípon názvů souborů a v otevřených FORMÁTECH XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Inteligentní značky jsou v aplikacích Excel 2010 a Word 2010 zastaralé. Proto pokud vaše řešení používá inteligentní značky, je nutné je odebrat předtím, než bude možné ho otestovat a ladit v Visual Studio 2013 nebo Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Upgradovat projekty systém Microsoft Office 2003
 K dispozici jsou další předpoklady pro upgrade přizpůsobení na úrovni dokumentu a doplňků VSTO, které cílí na systém Microsoft Office 2003.

### <a name="document-level-projects"></a>Projekty na úrovni dokumentu
 Pokud dokument v projektu obsahuje ovládací prvky model Windows Forms, musíte také mít nainstalováno Visual Studio 2005 Tools for Office Second Edition Runtime před upgradem projektu. Pokud tato verze modulu runtime není nainstalována na vývojovém počítači před upgradem projektu, upgradovaný projekt může obsahovat chyby kompilace nebo běhu. Po dokončení upgradu projektu můžete odinstalovat modul Visual Studio 2005 Tools for Office Second Edition Runtime z vývojového počítače, pokud ho nepoužívá žádná jiná řešení pro systém Office. Tato verze modulu runtime je k dispozici jako Distribuovatelný balíček z webu Microsoft Download Center v [nástroji Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 se) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

### <a name="vsto-add-in-projects"></a>Projekty doplňku VSTO
 Pokud soubor řešení pro původní projekt zahrnoval projekt instalace nebo InstallShield s omezením, který byl nakonfigurován pro instalaci doplňku VSTO, Visual Studio upgraduje projekt, ale neprovede žádné další změny projektu. Pokud chcete dál používat soubor Instalační služba systému Windows k nasazení doplňku VSTO, musíte upravit projekt instalace nebo InstallShield s omezením edice a nainstalovat tak nové požadavky, jako jsou [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , Visual Studio 2010 Tools for Office runtime a volitelně primární spolupracující sestavení, na která odkazuje doplněk VSTO. Další informace najdete v tématu [nasazení řešení pro Office pomocí Instalační služba systému Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 Pokud chcete použít ClickOnce k nasazení doplňku VSTO, můžete úplně odstranit projekt instalace nebo InstallShield Limited Edition. Další informace o nasazení doplňků VSTO pomocí technologie ClickOnce najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také
- [Postupy: upgrade řešení pro systém Office](/previous-versions/4bez6837(v=vs.140))
- [Migrace řešení Office na .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Upgrade projektu, dialogové okno Možnosti](../vsto/project-upgrade-options-dialog-box.md)