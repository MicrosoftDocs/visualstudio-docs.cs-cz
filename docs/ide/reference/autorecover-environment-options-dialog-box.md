---
title: AutoRecover, prostředí, dialogové okno Možnosti
description: Seznamte se s informacemi o automatickém obnovení, prostředí, možnostech a způsobu, jakým se používá k určení toho, jestli se mají soubory automaticky zálohovat.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 007e82ee7c1c2839ba266794432605f1f92a1669
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307788"
---
# <a name="autorecover-environment-options-dialog-box"></a>Automatické obnovení, prostředí, dialogové okno Možnosti

Tato stránka se používá v dialogovém okně **Možnosti** k určení, jestli se mají automaticky zálohovat soubory. Můžete také určit, jestli chcete obnovit změněné soubory, pokud se Visual Studio neočekávaně ukončí.

Chcete-li získat přístup k tomuto dialogovému oknu, přejděte do možnosti **nástroje**  >    >    >  **Automatické obnovení** prostředí.

:::image type="content" source="media/autorecover-options.png" alt-text="Snímek obrazovky s oddílem automatického obnovení v dialogovém okně Možnosti":::

**Ukládat informace automatického obnovení každých [n] min.**

::: moniker range=">=vs-2022"

Tuto možnost použijte, pokud chcete přizpůsobit, jak často se soubor v editoru automaticky ukládá. V případě dříve uložených souborů aplikace Visual Studio uloží kopii souboru do ***%localappdata%\Microsoft\VisualStudio\BackupFiles \\ [projectname]***. Pokud je soubor nový a zatím jste ho neuložili, Visual Studio ho automaticky uloží pomocí náhodně generovaného názvu souboru.

::: moniker-end

::: moniker range="vs-2019"

Tuto možnost použijte, pokud chcete přizpůsobit, jak často se soubor v editoru automaticky ukládá. V případě dříve uložených souborů aplikace Visual Studio 2019 verze 16,2 a novější uloží kopii souboru do ***%localappdata%\Microsoft\VisualStudio\BackupFiles \\ [projectname]***. Pokud je soubor nový a zatím jste ho neuložili, Visual Studio ho automaticky uloží pomocí náhodně generovaného názvu souboru.

> [!NOTE]
> Pokud používáte Visual Studio 2019 verze 16,1 nebo starší, umístění souboru je *%UserProfile%\Documents\Visual Studio [verze] \Backup Files \\ [projectname]*. Další informace naleznete na stránce historie zpráv k [vydání verzí sady Visual Studio 2019](/visualstudio/releases/2019/release-notes-history/) .

::: moniker-end

::: moniker range="vs-2017"

Tuto možnost použijte, pokud chcete přizpůsobit, jak často se soubor v editoru automaticky ukládá. V případě dříve uložených souborů bude Visual Studio 2017 ukládat kopii souboru v *%UserProfile%\Documents\Visual studiu [Version] \Backup Files \\ [projectname]*. Pokud je soubor nový a zatím jste ho neuložili, Visual Studio ho automaticky uloží pomocí náhodně generovaného názvu souboru.

::: moniker-end

**Zachovat informace automatického obnovení po dobu [n] dnů**

Tuto možnost použijte k určení, jak dlouho aplikace Visual Studio uchovává soubory vytvořené pro automatické obnovení.

### <a name="see-also"></a>Viz také

- [Možnosti – dialogové okno](../../ide/reference/options-dialog-box-visual-studio.md)
