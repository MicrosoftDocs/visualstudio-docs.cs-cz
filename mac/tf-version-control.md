---
title: Řízení verzí team foundation (TFVC)
description: Průvodce odstraňováním potíží o TFVC a macOS.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: e56aec03aabe818731c65acb30eafcc18f170ac3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714511"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Podporuje Visual Studio pro Mac Správu verzí Team Foundation?

> [!CAUTION]
> Rozšíření TFVC preview pro Visual Studio pro Mac už není ve Visual Studiu 2019 pro Mac podporované.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Možnosti alternativního správy verzí v Sadě Visual Studio pro Mac

Pro nejlepší prostředí správy verzí na macOS doporučujeme použít **Git** místo Řízení verzí Team Foundation (TFVC). 

Git je podporovaný ve Visual Studiu pro Mac a je výchozí možností pro úložiště hostovaná v Team Foundation Server (TFS)/Azure DevOps. Další informace o používání Gitu s TFS/Azure DevOps najdete v [tématu Nastavení úložiště Git](/visualstudio/mac/set-up-git-repository) průvodce.

## <a name="unsupported-workarounds-for-tfvc"></a>Nepodporovaná zástupná řešení pro TFVC

Zatímco Visual Studio pro Mac oficiálně nepodporuje TFVC, zbytek této příručky poskytuje některá řešení pro práci s TFVC v macOS. Pokud používáte TFVC pro správu verzí dnes, zde jsou některá řešení, která můžete použít pro přístup ke zdrojovému kódu hostovanému v TFVC:

* Možnost 1. [Použití kódu Visual Studia a rozšíření Azure Repos pro grafické uživatelské prostředí](#use-visual-studio-code-and-the-azure-repos-extension)
* Možnost 2. [Připojení k repo pomocí klienta Team Explorer everywhere Command Line Client (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>Možnost 1. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a>Použití kódu Visual Studia a rozšíření Azure Repos

Pokud chcete pracovat s grafickým rozhraním pro správu souborů ve správě verzí, pak rozšíření Azure Repos pro Visual Studio Code poskytuje podporované řešení od Microsoftu. Chcete-li začít, stáhněte si [kód Visual Studia](https://code.visualstudio.com) a přečtěte si, jak [nakonfigurovat rozšíření Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>Možnost 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Připojení pomocí klienta Team Explorer everywhere command line

> [!IMPORTANT]
> Podle průzkumníka týmu všude README, tento projekt [již není udržována](https://github.com/microsoft/team-explorer-everywhere).

Pokud jste spokojeni s používáním terminálu macOS, pak Team Explorer Everywhere Command Line Client (TEE-CLC) poskytuje podporovaný způsob připojení ke zdroji v TFVC.

Můžete postupovat podle následujících kroků nastavit připojení k TFVC a potvrdit změny.

#### <a name="setting-up-the-tee-clc"></a>Nastavení TEE-CLC

Existují dva způsoby, jak získat nastavení s TEE-CLC.

* Použijte Homebrew k instalaci klienta, nebo
* Stažení a ruční instalace klienta

Nejjednodušším řešením je **použití HomeBrew**, což je správce balíčků pro macOS. Postup instalace pomocí této metody:

1. Spusťte aplikaci terminálu macOS.
1. Nainstalujte Homebrew pomocí terminálu a pokyny na [domovské stránce Homebrew](https://brew.sh/).
1. Po instalaci homebrew spusťte z terminálu následující příkaz:`brew install tee-clc`

Ruční **nastavení TEE-CLC**:

1. [Stáhněte si nejnovější verzi tee-clc](https://github.com/Microsoft/team-explorer-everywhere/releases) ze stránky vydání team exploreru všude GitHub u pou (např. tee-clc-14.134.0.zip v době psaní tohoto článku).
1. Extrahujte obsah souboru ZIP do složky na disku.
1. Otevřete aplikaci terminál u `cd` macOS a pomocí příkazu přepněte do složky, kterou jste použili v předchozím kroku.
1. Ve složce spusťte `./tf` příkaz a otestujte, že klient příkazového řádku může být spuštěn, můžete být vyzváni k instalaci jazyka Java nebo jiných závislostí.

Po instalaci tee-CLC můžete spustit příkaz `tf eula` pro zobrazení a přijetí licenční smlouvy pro klienta.

Nakonec k ověření pomocí prostředí TFS/Azure DevOps, budete muset vytvořit osobní přístupový token na serveru. Přečtěte si další informace o [ověřování pomocí tokenů osobního přístupu](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Při vytváření osobního přístupového tokenu pro použití s TFVC, nezapomeňte poskytnout úplný přístup při konfiguraci tokenu.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Použití TEE-CLC pro připojení k repo

Chcete-li se připojit ke zdrojovému kódu, musíte `tf workspace` nejprve vytvořit pracovní prostor pomocí příkazu. Například následující příkazy se připojují k organizaci ve službách Azure DevOps s názvem "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Nastavení `TF_AUTO_SAVE_CREDENTIALS` prostředí se používá k uložení pověření, takže nebudete vyzváni k jejich zadání vícekrát. Po zobrazení výzvy k zadání uživatelského jména použijte osobní přístupový token, který jste vytvořili v předchozí části, a použijte prázdné heslo.

Chcete-li vytvořit mapování zdrojových souborů do místní složky, použijete `tf workfold` příkaz. Následující příklad namapuje složku s názvem "WebApp.Services" z projektu TFVC "MyRepository" a nastaví ji tak, aby byla zkopírována do místní složky ~/Projects/ (tj. složka "Projekty" v domovské složce aktuálního uživatele).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Nakonec pomocí následujícího příkazu získáte zdrojové soubory ze serveru a zkopírujete je místně:

```bash
tf get
```

#### <a name="committing-changes-using-the-tee-clc"></a>Potvrzení změn pomocí TEE-CLC

Po provedené maškarních souborech ve Visual Studiu for Mac můžete přepnout zpět na terminál a vrátit se změnami. Příkaz `tf add` se používá k přidání souborů do seznamu čekajících změn, `tf checkin` které mají být zpět,a příkaz provede skutečné vrácení se změnami na server. Příkaz `checkin` obsahuje parametry pro přidání komentáře nebo přidružení související pracovní položky. V následujícím fragmentu kódu jsou všechny `WebApp.Services` soubory ve složce přidány rekurzivně do vrácení se změnami. Poté je kód se změnami s komentářem a přidružen k pracovní položce s ID "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Chcete-li se dozvědět více o zde uvedených příkazech nebo jiných, můžete použít následující příkaz z terminálu:

`tf help`

## <a name="see-also"></a>Viz také

- [Vývoj a sdílení kódu v TFVC pomocí Visual Studia (ve Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)