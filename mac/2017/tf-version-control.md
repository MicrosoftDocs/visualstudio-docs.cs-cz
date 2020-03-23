---
title: Řízení verzí team foundation (TFVC)
description: Připojení z Visual Studia pro Mac na Team Foundation Server/Azure DevOps s team foundation správy verzí (TFVC).
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: b7b160d58cead031a0eece2a522501d8c2060bd2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985196"
---
# <a name="connecting-to-team-foundation-version-control"></a>Připojení ke sněmu verzí Team Foundation

> [!NOTE]
> Pro nejlepší prostředí správy verzí na macOS doporučujeme použít Git místo Řízení verzí Team Foundation (TFVC). Git je podporovaný ve Visual Studiu pro Mac a je výchozí možností pro úložiště hostovaná v Team Foundation Server (TFS)/Azure DevOps. Další informace o používání Gitu s TFS/Azure DevOps najdete v článku [Nastavení úložiště Git.](/visualstudio/mac/set-up-git-repository)
>
> Pokud jste dříve používali předběžnou verzi rozšíření TFVC pro Visual Studio pro Mac, už není podporovaná při upgradu na Visual Studio 2019 pro Mac.

Azure Repos poskytuje dva modely správy verzí: [Git](/azure/devops/repos/git/?view=azure-devops), distribuovaný systém správy verzí a [řízení verzí Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), centralizovaný systém správy verzí.

Visual Studio pro Mac poskytuje plnou podporu pro úložiště Git, ale vyžaduje určitá řešení pro práci s TFVC. Pokud používáte TFVC pro správu verzí dnes, zde jsou některá řešení, která můžete použít pro přístup ke zdrojovému kódu hostovanému v TFVC:

* [Použití kódu Visual Studia a rozšíření Azure Repos pro grafické uživatelské prostředí](#use-visual-studio-code-and-the-azure-repos-extension)
* [Připojení k repo pomocí klienta Team Explorer everywhere Command Line Client (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Připojení k TFVC pomocí (nepodporovaného) rozšíření Správy verzí Team Foundation pro Visual Studio for Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Zbytek tohoto článku vás provede výše uvedenými možnostmi.

## <a name="requirements"></a>Požadavky

* Visual Studio Community, Professional nebo Enterprise pro Mac verze 7.8 a novější.
* Azure DevOps Services, Team Foundation Server 2013 a novější nebo Azure DevOps Server 2018 a novější.
* Projekt ve službách Azure DevOps Services nebo Team Foundation Server/Server Azure DevOps, nakonfigurovaný pro použití správy verzí Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Použití kódu Visual Studia a rozšíření Azure Repos

Pokud chcete pracovat s grafickým rozhraním pro správu souborů ve správě verzí, pak rozšíření Azure Repos pro Visual Studio Code poskytuje podporované řešení od Microsoftu. Chcete-li začít, stáhněte si [kód Visual Studia](https://code.visualstudio.com) a přečtěte si, jak [nakonfigurovat rozšíření Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Připojení pomocí klienta Team Explorer everywhere command line

Pokud jste spokojeni s používáním terminálu macOS, pak Team Explorer Everywhere Command Line Client (TEE-CLC) poskytuje podporovaný způsob připojení ke zdroji v TFVC.

Můžete postupovat podle následujících kroků nastavit připojení k TFVC a potvrdit změny.

### <a name="setting-up-the-tee-clc"></a>Nastavení TEE-CLC

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

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Použití TEE-CLC pro připojení k repo

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

### <a name="committing-changes-using-the-tee-clc"></a>Potvrzení změn pomocí TEE-CLC

Po provedené maškarních souborech ve Visual Studiu for Mac můžete přepnout zpět na terminál a vrátit se změnami. Příkaz `tf add` se používá k přidání souborů do seznamu čekajících změn, `tf checkin` které mají být zpět,a příkaz provede skutečné vrácení se změnami na server. Příkaz `checkin` obsahuje parametry pro přidání komentáře nebo přidružení související pracovní položky. V následujícím fragmentu kódu jsou všechny `WebApp.Services` soubory ve složce přidány rekurzivně do vrácení se změnami. Poté je kód se změnami s komentářem a přidružen k pracovní položce s ID "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Chcete-li se dozvědět více o zde uvedených příkazech nebo jiných, můžete použít následující příkaz z terminálu:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Připojení k TFVC pomocí rozšíření Team Foundation Version Control

> [!NOTE]
> Pro nejlepší prostředí správy verzí na macOS doporučujeme použít Git místo Řízení verzí Team Foundation (TFVC). Git je podporovaný ve Visual Studiu pro Mac a je výchozí možností pro úložiště hostovaná v Team Foundation Server (TFS)/Azure DevOps. Další informace o používání Gitu s TFS/Azure DevOps najdete v článku [Nastavení úložiště Git.](/visualstudio/mac/set-up-git-repository)
>
> Pokud jste dříve používali předběžnou verzi rozšíření TFVC pro Visual Studio pro Mac, už není podporovaná při upgradu na Visual Studio 2019 pro Mac.

V galerii rozšíření Visual Studio pro Mac je rozšíření pro správu verzí Team Foundation, které nabízí omezenou podporu pro připojení k TFVC. Rozšíření není podporováno a má několik známých problémů, takže vaše zkušenosti se mohou lišit při jeho použití.

Pokud chcete rozšíření nainstalovat, spusťte Visual Studio for Mac a zvolte nabídku **Visual Studio > Extensions.** Na kartě **Galerie** vyberte **správa verzí > správa verzí Team Foundation pro TFS a Azure DevOps** a klikněte na **Instalovat...**:

![Správce rozšíření](media/tfvc-install.png)

Podle pokynů nainstalujte rozšíření. Po instalaci restartujte ide.

### <a name="updating-the-extension"></a>Aktualizace rozšíření

Aktualizace rozšíření TFVC jsou prováděny pravidelně. Chcete-li získat přístup k aktualizacím, zvolte v nabídce rozšíření > rozšíření sady **Update** Visual **Studio** a vyberte kartu **Aktualizace.**

Stisknutím tlačítka **Instalovat** v dalším dialogovém okně odinstalujte starý balíček a nainstalujte nový.

### <a name="using-the-extension"></a>Použití rozšíření

Po instalaci rozšíření vyberte **> správy verzí TFS/Azure DevOps > otevřít ze vzdáleného úložiště... položku** nabídky.

![Položka nabídky pro otevření rozšíření](media/tfvc-source-control-explorer-devops.png)

Chcete-li začít, zvolte buď VSTS nebo Team Foundation Server, a stiskněte **tlačítko Pokračovat**:

![Připojení k serveru](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Azure Repos ověřování

Když vyberete projekt, který je hostovaný v Azure Repos, budete vyzváni k zadání podrobností o účtu Microsoft:

![Propojení s Azure Repos](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>Ověřování TFS

Chcete-li se připojit k serveru TFS, zadejte podrobnosti o serveru a přihlašovací údaje k účtu. Zadejte doménu, která má používat ověřování NTLM, jinak ponechte prázdné, chcete-li použít základní ověřování. Vyberte **Přidat server**:

![Přihlášení k serveru TFS](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Výběr projektu

Po úspěšném ověření se seznam úložišť přidružených k účtu zobrazí v dialogovém okně **Otevřít ze správy zdrojového kódu:**

![Otevřít z dialogového okna Řízení zdrojového kódu se zobrazenými projekty](media/tfvc-vsts-projects.png)

Toto dialogové okno je uspořádáno s následujícími uzly:

- Organizace nebo kolekce Azure DevOps – zobrazí se všechny organizace připojené k účtu Microsoft, se kterým jste se přihlásili.
- Projekty - V každé organizaci nebo kolekci můžete mít několik projektů. Projekt je místo, kde jsou hostovány zdrojový kód, pracovní položky a automatizovaná sestavení.

V tomto okamžiku můžete vyhledávat a filtrovat podle názvu projektu nebo organizace.

#### <a name="adding-a-new-server"></a>Přidání nového serveru

Chcete-li do seznamu přidat nový server, stiskněte tlačítko **Přidat hostitele** v dialogovém okně Otevřít ze **správy zdrojového kódu:**

![Zvýrazněné tlačítko Přidat pro přidání nového serveru do seznamu](media/tfvc-add-new-server.png)

Vyberte poskytovatele ze seznamu a zadejte přihlašovací údaje:

![Dialogové okno zobrazující možnost pro zprostředkovatele správy zdrojového kódu](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Vytvoření nového pracovního prostoru

Chcete-li začít pracovat s projektem, musíte mít _pracovní prostor_. Pokud ještě pracovní prostor nemáte, můžete ho vytvořit ze společního pole **Pracovní prostor** v dialogovém okně Otevřít ze **správy zdrojového kódu:**

![Vytvořit novou možnost seseznamem pracovního prostoru](media/tfvc-create-new-workspace.png)

Nastavte název a místní cestu pro nový pracovní prostor a vyberte **Vytvořit pracovní prostor**:

![Zadání názvu a místní cesty pro nový pracovní prostor](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Použití Průzkumníka zdrojového kódu

Po vytvoření pracovního prostoru a namapování projektu můžete začít pracovat s _Průzkumníkem zdrojového kódu_.

Chcete-li otevřít Průzkumník zdrojového kódu, vyberte > položku nabídky **tfs/Azure DevOps > průzkumník správy dat.**

Průzkumník zdrojového kódu umožňuje procházet všechny mapované projekty, jejich soubory a složky. Umožňuje také provádět všechny základní akce správy zdrojového kódu, například:

- Získejte nejnovější verzi
- Získání konkrétní verze
- Rezervace souborů a vrácení souborů se změnami
- Uzamčení a odemknutí souborů
- Přidání, odstranění a přejmenování souborů
- Zobrazení historie
- Porovnejte změny.

Mnohé z těchto akcí jsou k dispozici prostřednictvím kontextových akcí v projektu:

![Akce kontextové nabídky pro projekt](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Správa pracovních prostorů

Pokud jste ještě nevytvořili pracovní prostor, jak je popsáno v části [Vytvoření pracovního prostoru,](#creating-a-new-workspace) zjistíte, že Průzkumník zdrojového kódu je prázdný:

![prázdný průzkumník zdrojového kódu](media/tfvc-setup-empty-sce.png)

Chcete-li vzdálený projekt nastavit v místním pracovním prostoru, postupujte takto:

1. Vyberte **server** ze seseznamu.
1. Všimněte si, že existují "žádné pracovní prostory" a že místní cesta je "Není mapováno". Vyberte odkaz **Nenamapovat,** chcete-li zobrazit dialogové okno **Vytvořit nový pracovní prostor.**
1. Zadejte název pracovního prostoru a kliknutím na **Přidat pracovní složku** namapujte projekt na místní složku v počítači:

    ![Vytvoření nového dialogového okna pracovního prostoru s výchozími možnostmi](media/tfvc-workspace1.png)

1. Vyberte složku $, chcete-li mapovat všechny projekty na serveru na stejný pracovní prostor, nebo vyberte jednotlivý projekt a klepněte na tlačítko **OK**:

    ![Dialogové okno Vyhledat složku zobrazující všechny projekty](media/tfvc-workspace2.png)

1. Vyberte umístění v místním počítači, na které chcete projekt (projekty) namapovat, a klepněte na tlačítko **Vybrat složku**.
1. Potvrďte podrobnosti nového pracovního prostoru stisknutím **tlačítka OK**

    ![Dialogové okno Vytvořit nový pracovní prostor s přidanou pracovní složkou](media/tfvc-workspace3.png)

Jakmile je pracovní prostor nastaven, můžete jej změnit nebo odebrat kliknutím na tlačítko **Spravovat pracovní prostory** v Průzkumníku zdrojového kódu.

![Správa pracovních prostorů](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Odstraňování potíží a známé problémy

#### <a name="problems-using-basic-authentication"></a>Problémy s používáním základního ověřování

K ověření pomocí serveru lze použít následující možnosti:

- Oauth
- Basic
- Ntlm

Chcete-li použít základní ověřování, je nutné povolit **alternativní ověřování pověření** ve službě Azure DevOps Services, a to podle následujících kroků:

1. Přihlaste se ke své organizaci Azure DevOps jako vlastník (https:\//dev.azure.com/{organization}/{project}).

2. Na panelu nástrojů organizace vyberte ikonu ozubeného kola a vyberte **Zásady**:

    ![Vybraná možnost nastavení zásad](media/tfvc-auth2.png)

3. Zkontrolujte nastavení připojení aplikace. Na základě zásad zabezpečení můžete změnit tato nastavení:

    ![Vybraná možnost nastavení zásad](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>Nevidím nic v TFVC

Chcete-li nastavit řízení verzí team foundation (TFVC) na vašem dev počítači, **musíte** vytvořit pracovní prostor, jak je popsáno v části [Správa pracovních prostorů.](#managing-workspaces)

V Průzkumníku ovládacích zdrojů stiskněte tlačítko **Spravovat pracovní prostory.** Podle pokynů namapujte projekt na složku na počítači s dev.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Nevidím žádné / všechny mé projekty

Po ověření byste měli vidět seznam projektů. Ve výchozím nastavení jsou zobrazeny pouze projekty TFS. Chcete-li zobrazit další typy projektů, zaškrtněte políčko Zobrazit všechny projekty.

Mějte na paměti, že projekty, které jsou na serveru se nezobrazí, pokud nemáte správná oprávnění.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Zobrazuje se chyba "Nelze vytvořit pracovní prostor. Prosím, zkuste to znovu"

Při [pokusu o vytvoření nového pracovního prostoru](#creating-a-new-workspace)byste se měli ujistit, že jsou splněny následující podmínky:

- V názvu pracovního prostoru není použití neplatných znaků.
- Název musí být menší než 64 znaků.
- Místní cestu nelze použít jinými pracovními prostory.

### <a name="see-also"></a>Viz také

- [Vývoj a sdílení kódu v TFVC pomocí Visual Studia (ve Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)