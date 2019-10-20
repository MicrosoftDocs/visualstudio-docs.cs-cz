---
title: AutoRecover, prostředí, dialogové okno Možnosti
ms.date: 11/04/2016
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865cf2ec43071a01a333961e118beab14abab82b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651897"
---
# <a name="autorecover-environment-options-dialog-box"></a>Automatické obnovení, prostředí, dialogové okno Možnosti

Tato stránka se používá v dialogovém okně **Možnosti** k určení, jestli se mají automaticky zálohovat soubory. Můžete také určit, jestli chcete obnovit změněné soubory, pokud se Visual Studio neočekávaně ukončí.

K tomuto dialogovému oknu se dostanete tak, že vyberete nabídku **nástroje** , vyberete **Možnosti**a pak vyberete **prostředí**  > **Automatické obnovení**. Pokud se tato stránka v seznamu nezobrazuje, vyberte v dialogovém okně **Možnosti** možnost **Zobrazit všechna nastavení** .

**Ukládat informace automatického obnovení každých [n] min.**

Tuto možnost použijte, pokud chcete přizpůsobit, jak často se soubor v editoru automaticky ukládá. V případě dříve uložených souborů je kopie souboru uložena v *%UserProfile%\Documents\Visual studiu \\ [Version] \Backup files \\ [projectname]* . Pokud je soubor nový a zatím jste ho neuložili, soubor se automaticky uloží pomocí náhodně generovaného názvu souboru.

**Zachovat informace automatického obnovení po dobu [n] dnů**

Tuto možnost použijte k určení, jak dlouho aplikace Visual Studio uchovává soubory vytvořené pro automatické obnovení.

### <a name="see-also"></a>Viz také:

- [Dialogové okno Možnosti](../../ide/reference/options-dialog-box-visual-studio.md)