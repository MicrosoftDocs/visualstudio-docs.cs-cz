---
title: Automatické obnovení, prostředí, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 743543e03806a842eabc2bbfc69011d63b1264d0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660968"
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoRecover, prostředí, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato stránka dialogového okna možnosti slouží k určení, zda jsou soubory automaticky zálohovány. Tato stránka také umožňuje určit, jestli se mají změněné soubory obnovit v případě neočekávaného vypnutí integrovaného vývojového prostředí (IDE). K tomuto dialogovému oknu se dostanete tak, že vyberete nabídku **nástroje** a zvolíte **Možnosti**a pak vyberete složku **prostředí** a kliknete na stránku pro **Automatické obnovení** . Pokud se tato stránka v seznamu nezobrazuje, vyberte v dialogovém okně **Možnosti** možnost **Zobrazit všechna nastavení** .

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Ukládat informace automatického obnovení každých \<n > minut** Tuto možnost použijte, pokud chcete přizpůsobit, jak často se soubor v editoru automaticky ukládá. V případě dříve uložených souborů se kopie souboru uloží do \\. ..\My Documents\Visual Studio \<*verze*> soubory \Backup \\ <*ProjectName*>. Pokud je soubor nový a nebyl uložen ručně, soubor bude automaticky uložen pomocí náhodně generovaného názvu souboru.

 **Zachovat informace o automatickém obnovení pro \<n > dny** Tuto možnost použijte k určení, jak dlouho aplikace Visual Studio uchovává soubory vytvořené pro automatické obnovení.

## <a name="see-also"></a>Viz také
 [Dialogové okno Možnosti](../../ide/reference/options-dialog-box-visual-studio.md)
