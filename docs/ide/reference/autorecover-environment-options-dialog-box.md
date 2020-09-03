---
title: AutoRecover, prostředí, dialogové okno Možnosti
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f35424089b293b858c609d19f59459693373eb4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250293"
---
# <a name="autorecover-environment-options-dialog-box"></a>Automatické obnovení, prostředí, dialogové okno Možnosti

Tato stránka se používá v dialogovém okně **Možnosti** k určení, jestli se mají automaticky zálohovat soubory. Můžete také určit, jestli chcete obnovit změněné soubory, pokud se Visual Studio neočekávaně ukončí.

Chcete-li získat přístup k tomuto dialogovému oknu, přejděte do možnosti **nástroje**  >  **Options**  >  **Environment**  >  **Automatické obnovení**prostředí.

:::image type="content" source="media/autorecover-options.png" alt-text="Snímek obrazovky s oddílem automatického obnovení v dialogovém okně Možnosti":::

**Ukládat informace automatického obnovení každých [n] min.**

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
