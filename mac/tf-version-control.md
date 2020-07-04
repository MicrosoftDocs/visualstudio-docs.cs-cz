---
title: Správa verzí Team Foundation (TFVC)
description: Průvodce odstraňováním potíží s TFVC a macOS.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: c51f3cd50598cd0c33b019c09f95554cc5f9058b
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950501"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Podporuje Visual Studio pro Mac Správu verzí Team Foundation?

> [!CAUTION]
> Rozšíření TFVC verze Preview pro Visual Studio pro Mac již není podporováno v aplikaci Visual Studio 2019 for Mac.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Alternativní možnosti řízení verze v Visual Studio pro Mac

K dosažení nejlepšího prostředí pro správu verzí na macOS doporučujeme použít **Git** místo Správa verzí Team Foundation (TFVC). 

V Visual Studio pro Mac se podporuje Git a je výchozí možností pro úložiště hostovaná v Team Foundation Server (TFS)/Azure DevOps. Další informace o použití Gitu s TFS/Azure DevOps najdete v tématu Nastavení příručky pro [úložiště Git](/visualstudio/mac/set-up-git-repository) .

## <a name="unsupported-workarounds-for-tfvc"></a>Nepodporovaná řešení pro TFVC

I když Visual Studio pro Mac TFVC oficiálně nepodporuje, zbývající část tohoto průvodce poskytuje několik alternativních řešení pro práci s TFVC v macOS. Pokud dnes používáte TFVC pro řízení verzí, tady je několik řešení, která můžete použít pro přístup ke zdrojovému kódu hostovanému v TFVC:

* Možnost 1. [Použití Visual Studio Code a rozšíření Azure Repos pro grafické uživatelské rozhraní](#use-visual-studio-code-and-the-azure-repos-extension)
* Možnost 2. [Připojte se k úložišti pomocí Team Explorer Everywhere klienta příkazového řádku (TEE-CLC).](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>Možnost 1. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a>Použití Visual Studio Code a rozšíření Azure Repos

Pokud chcete pracovat s grafickým rozhraním pro správu souborů ve správě verzí, pak rozšíření Azure Repos pro Visual Studio Code poskytuje podporované řešení od společnosti Microsoft. Začněte tím, že si stáhnete [Visual Studio Code](https://code.visualstudio.com) a pak zjistíte, jak [nakonfigurovat Azure Repos rozšíření](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>Možnost 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Připojení pomocí klienta příkazového řádku Team Explorer Everywhere

> [!IMPORTANT]
> Na základě souboru READme Team Explorer Everywhere se tento projekt [už neudržuje](https://github.com/microsoft/team-explorer-everywhere).

Pokud jste obeznámeni s používáním terminálu macOS, pak klient příkazového řádku Team Explorer Everywhere (TEE-CLC) poskytuje podporovaný způsob, jak se připojit ke zdroji v TFVC.

Pomocí následujících kroků můžete nastavit připojení tak, aby se TFVC, a potvrdit změny.

#### <a name="setting-up-the-tee-clc"></a>Nastavení TEE-CLC

Existují dva způsoby, jak pomocí TEE-CLC získat instalační program.

* K instalaci klienta použijte homebrew nebo
* Stažení a ruční instalace klienta

Nejjednodušším řešením je **použití HomeBrew**, což je správce balíčků pro MacOS. Postup instalace pomocí této metody:

1. Spusťte aplikaci macOS Terminal.
1. Nainstalujte homebrew pomocí terminálu a pokynů na [domovské stránce homebrew](https://brew.sh/).
1. Po instalaci homebrew spusťte z terminálu následující příkaz:`brew install tee-clc`

**Ruční nastavení Tee-CLC**:

1. [Stáhněte si nejnovější verzi Tee-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) ze Team Explorer Everywhere stránky vydání úložiště GitHub (např. tee-clc-14.134.0.zip v době psaní tohoto zápisu).
1. Extrahujte obsah souboru. zip do složky na disku.
1. Otevřete aplikaci terminálu macOS a pomocí `cd` příkazu přejděte do složky, kterou jste použili v předchozím kroku.
1. V rámci této složky spusťte příkaz `./tf` pro otestování, zda lze spustit klienta příkazového řádku, může se zobrazit výzva k instalaci jazyka Java nebo jiných závislostí.

Po instalaci TEE-CLC můžete spustit příkaz `tf eula` a zobrazit a přijmout licenční smlouvu pro klienta.

Nakonec, pokud chcete ověřit své prostředí TFS nebo Azure DevOps, musíte na serveru vytvořit osobní přístupový token. Přečtěte si další informace o [ověřování pomocí tokenů osobních přístupů](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Při vytváření osobního přístupového tokenu pro použití s TFVC se ujistěte, že při konfiguraci tokenu zadáte úplný přístup.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Připojení k úložišti pomocí TEE-CLC

Abyste se mohli připojit ke svému zdrojovému kódu, musíte nejprve vytvořit pracovní prostor pomocí `tf workspace` příkazu. Například následující příkazy se připojují k organizaci v Azure DevOps Services s názvem "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS`Nastavení prostředí slouží k uložení vašich přihlašovacích údajů, takže se k nim nebudete muset zadávat víckrát. Po zobrazení výzvy k zadání uživatelského jména použijte token osobní přístup, který jste vytvořili v předchozí části, a použijte prázdné heslo.

Chcete-li vytvořit mapování zdrojových souborů do místní složky, použijte `tf workfold` příkaz. Následující příklad mapuje složku s názvem "WebApp. Services" z projektu "MyRepository" TFVC a nastaví ji tak, aby byla zkopírována do místní složky ~/Projects/(tj. složka "projekty" v domovské složce aktuálního uživatele).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Nakonec pomocí následujícího příkazu načtete zdrojové soubory ze serveru a zkopírujete je místně:

```bash
tf get
```

#### <a name="committing-changes-using-the-tee-clc"></a>Potvrzování změn pomocí TEE-CLC

Až provedete změny souborů v Visual Studio pro Mac, můžete přejít zpět na terminál a vrátit se změnami provedené úpravy. `tf add`Příkaz slouží k přidání souborů do seznamu probíhajících změn, které mají být vráceny se změnami, a `tf checkin` příkaz provede skutečné vrácení se změnami na server. `checkin`Příkaz obsahuje parametry pro přidání komentáře nebo k přidružení související pracovní položky. V následujícím fragmentu kódu jsou všechny soubory ve `WebApp.Services` složce přidány rekurzivně do vrácení se změnami. Pak je kód vrácen se změnami pomocí komentáře a přidružen k pracovní položce s ID "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Pokud chcete získat další informace o uvedených příkazech nebo jiných, můžete použít následující příkaz z terminálu:

`tf help`

## <a name="see-also"></a>Viz také

- [Vývoj a sdílení kódu v TFVC pomocí sady Visual Studio (ve Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)