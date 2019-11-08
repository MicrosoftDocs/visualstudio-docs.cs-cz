---
title: Správa verzí Team Foundation (TFVC)
description: Připojení z Visual Studio pro Mac k Team Foundation Server/Azure DevOps s Správa verzí Team Foundation (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: e45f80ab1a5aab4969b01a2fddcfd88d9dc4eff7
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73716132"
---
# <a name="connecting-to-team-foundation-version-control"></a>Připojování k Správa verzí Team Foundation

> [!NOTE]
> K dosažení nejlepšího prostředí pro správu verzí na macOS doporučujeme použít Git místo Správa verzí Team Foundation (TFVC). V Visual Studio pro Mac se podporuje Git a je výchozí možností pro úložiště hostovaná v Team Foundation Server (TFS)/Azure DevOps. Další informace o použití Gitu s TFS/Azure DevOps najdete v článku [Nastavení úložiště Git](/visualstudio/mac/set-up-git-repository) .
>
> Pokud jste dříve používali verzi Preview rozšíření TFVC pro Visual Studio pro Mac, při upgradu na sadu Visual Studio 2019 pro Mac už není podporována.

Azure Repos poskytuje dva modely správy verzí: [Git](/azure/devops/repos/git/?view=azure-devops), distribuovaný systém správy verzí a [Správa verzí Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), centralizovaný systém správy verzí.

Visual Studio pro Mac poskytuje úplnou podporu úložišť Git, ale vyžaduje některá alternativní řešení pro práci s TFVC. Pokud dnes používáte TFVC pro řízení verzí, tady je několik řešení, která můžete použít pro přístup ke zdrojovému kódu hostovanému v TFVC:

* [Použití Visual Studio Code a rozšíření Azure Repos pro grafické uživatelské rozhraní](#use-visual-studio-code-and-the-azure-repos-extension)
* [Připojte se k úložišti pomocí Team Explorer Everywhere klienta příkazového řádku (TEE-CLC).](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Připojení k TFVC pomocí rozšíření (nepodporované) Správa verzí Team Foundation pro Visual Studio pro Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Zbytek tohoto článku vás provede výše uvedenými možnostmi.

## <a name="requirements"></a>Požadavky

* Visual Studio Community, Professional nebo Enterprise for Mac verze 7,8 a novější.
* Azure DevOps Services, Team Foundation Server 2013 a novější, nebo Azure DevOps Server 2018 a novější.
* Projekt v Azure DevOps Services nebo Team Foundation Server/Azure DevOps Server nakonfigurovaný pro použití Správa verzí Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Použití Visual Studio Code a rozšíření Azure Repos

Pokud chcete pracovat s grafickým rozhraním pro správu souborů ve správě verzí, pak rozšíření Azure Repos pro Visual Studio Code poskytuje podporované řešení od společnosti Microsoft. Začněte tím, že si stáhnete [Visual Studio Code](https://code.visualstudio.com) a pak zjistíte, jak [nakonfigurovat Azure Repos rozšíření](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Připojení pomocí klienta příkazového řádku Team Explorer Everywhere

Pokud jste obeznámeni s používáním terminálu macOS, pak klient příkazového řádku Team Explorer Everywhere (TEE-CLC) poskytuje podporovaný způsob, jak se připojit ke zdroji v TFVC.

Pomocí následujících kroků můžete nastavit připojení tak, aby se TFVC, a potvrdit změny.

### <a name="setting-up-the-tee-clc"></a>Nastavení TEE-CLC

Existují dva způsoby, jak pomocí TEE-CLC získat instalační program.

* K instalaci klienta použijte homebrew nebo
* Stažení a ruční instalace klienta

Nejjednodušším řešením je **použití HomeBrew**, což je správce balíčků pro MacOS. Postup instalace pomocí této metody:

1. Spusťte aplikaci macOS Terminal.
1. Nainstalujte homebrew pomocí terminálu a pokynů na [domovské stránce homebrew](https://brew.sh/).
1. Po instalaci homebrew spusťte z terminálu následující příkaz: `brew install tee-clc`

**Ruční nastavení Tee-CLC**:

1. [Stáhněte si nejnovější verzi Tee-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) ze Team Explorer Everywhere stránky vydání úložiště GitHub (např. tee-CLC-14.134.0. zip v době psaní tohoto zápisu).
1. Extrahujte obsah souboru. zip do složky na disku.
1. Otevřete aplikaci terminálu macOS a pomocí příkazu `cd` přepněte do složky, kterou jste použili v předchozím kroku.
1. V rámci složky spusťte `./tf` příkazu, abyste otestovali, že je možné spustit klienta příkazového řádku, může se zobrazit výzva k instalaci Java nebo jiných závislostí.

Po instalaci TEE-CLC můžete spustit příkaz `tf eula` a zobrazit a přijmout licenční smlouvu pro klienta.

Nakonec, pokud chcete ověřit své prostředí TFS nebo Azure DevOps, musíte na serveru vytvořit osobní přístupový token. Přečtěte si další informace o [ověřování pomocí tokenů osobních přístupů](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Při vytváření osobního přístupového tokenu pro použití s TFVC se ujistěte, že při konfiguraci tokenu zadáte úplný přístup.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Připojení k úložišti pomocí TEE-CLC

Abyste se mohli připojit ke svému zdrojovému kódu, musíte nejprve vytvořit pracovní prostor pomocí příkazu `tf workspace`. Například následující příkazy se připojují k organizaci v Azure DevOps Services s názvem "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Nastavení prostředí `TF_AUTO_SAVE_CREDENTIALS` slouží k uložení vašich přihlašovacích údajů, takže se k nim nebudete muset zadávat víckrát. Po zobrazení výzvy k zadání uživatelského jména použijte token osobní přístup, který jste vytvořili v předchozí části, a použijte prázdné heslo.

Chcete-li vytvořit mapování zdrojových souborů do místní složky, použijte příkaz `tf workfold`. Následující příklad mapuje složku s názvem "WebApp. Services" z projektu "MyRepository" TFVC a nastaví ji tak, aby byla zkopírována do místní složky ~/Projects/(tj. složka "projekty" v domovské složce aktuálního uživatele).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Nakonec pomocí následujícího příkazu načtete zdrojové soubory ze serveru a zkopírujete je místně:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Potvrzování změn pomocí TEE-CLC

Až provedete změny souborů v Visual Studio pro Mac, můžete přejít zpět na terminál a vrátit se změnami provedené úpravy. Příkaz `tf add` slouží k přidání souborů do seznamu probíhajících změn, které mají být vráceny se změnami, a příkaz `tf checkin` provede skutečné vrácení se změnami na server. Příkaz `checkin` obsahuje parametry pro přidání komentáře nebo k přidružení související pracovní položky. V následujícím fragmentu kódu jsou všechny soubory ve složce `WebApp.Services` přidány rekurzivně na vrácení se změnami. Pak je kód vrácen se změnami pomocí komentáře a přidružen k pracovní položce s ID "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Pokud chcete získat další informace o uvedených příkazech nebo jiných, můžete použít následující příkaz z terminálu:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Připojení k TFVC pomocí rozšíření Správa verzí Team Foundation

> [!NOTE]
> K dosažení nejlepšího prostředí pro správu verzí na macOS doporučujeme použít Git místo Správa verzí Team Foundation (TFVC). V Visual Studio pro Mac se podporuje Git a je výchozí možností pro úložiště hostovaná v Team Foundation Server (TFS)/Azure DevOps. Další informace o použití Gitu s TFS/Azure DevOps najdete v článku [Nastavení úložiště Git](/visualstudio/mac/set-up-git-repository) .
>
> Pokud jste dříve používali verzi Preview rozšíření TFVC pro Visual Studio pro Mac, při upgradu na sadu Visual Studio 2019 pro Mac už není podporována.

V galerii rozšíření Visual Studio pro Mac existuje rozšíření pro řízení verzí Team Foundation, které nabízí omezené podpory pro připojení k TFVC. Toto rozšíření se nepodporuje a má několik známých problémů, takže se při jeho použití může lišit vaše prostředí.

Pokud chcete nainstalovat rozšíření, spusťte Visual Studio pro Mac a vyberte nabídku **rozšíření pro Visual Studio >** . Na kartě **Galerie** vyberte možnost správa **verzí > Správa verzí Team Foundation pro TFS a Azure DevOps** a klikněte na **nainstalovat...** :

![Správce rozšíření](media/tfvc-install.png)

Postupujte podle pokynů k instalaci rozšíření. Po instalaci restartujte IDE.

### <a name="updating-the-extension"></a>Aktualizace rozšíření

Aktualizace rozšíření TFVC jsou pravidelně prováděny. Chcete-li získat přístup k aktualizacím, zvolte **rozšíření sady Visual Studio >...** v nabídce a vyberte kartu **aktualizace** . Vyberte rozšíření v seznamu a stiskněte tlačítko **aktualizovat** :

Stisknutím tlačítka **nainstalovat** v dalším dialogovém okně odinstalujte starý balíček a nainstalujte nový.

### <a name="using-the-extension"></a>Použití rozšíření

Po instalaci rozšíření vyberte **řízení verze > TFS/Azure DevOps > otevřít ze vzdáleného úložiště...** položka nabídky.

![Položka nabídky pro otevření rozšíření](media/tfvc-source-control-explorer-devops.png)

Začněte tím, že zvolíte buď VSTS, nebo Team Foundation Server, a stiskněte **pokračovat**:

![Připojení k serveru](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Ověřování Azure Repos

Když vyberete projekt, který je hostovaný na Azure Repos, zobrazí se výzva k zadání podrobností účet Microsoft:

![Připojení pomocí Azure Repos](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>Ověřování TFS

Pokud se chcete připojit k TFS, zadejte podrobnosti o serveru a přihlašovací údaje k vašemu účtu. Zadejte doménu pro použití ověřování NTLM, jinak ponechte prázdné pro použití základního ověřování. Vyberte **Přidat server**:

![Přihlášení k serveru TFS](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Výběr projektu

Po úspěšném ověření uvidíte seznam úložišť, která jsou přidružená k účtu, v dialogovém okně **Otevřít ze správy zdrojového kódu** :

![Otevřít v dialogovém okně správy zdrojového kódu se zobrazenými projekty](media/tfvc-vsts-projects.png)

Toto dialogové okno je uspořádáno pomocí následujících uzlů:

- Organizace nebo kolekce Azure DevOps – zobrazuje všechny organizace, které jsou připojené k účet Microsoft jste se přihlásili.
- Projekty – v každé organizaci nebo kolekci můžete mít několik projektů. Projekt je místo, kde je hostovaný zdrojový kód, pracovní položky a automatizovaná sestavení.

V tuto chvíli můžete hledat a filtrovat podle názvu projektu nebo organizace.

#### <a name="adding-a-new-server"></a>Přidání nového serveru

Pokud chcete do seznamu přidat nový server, stiskněte tlačítko **Přidat hostitele** v dialogovém okně **Otevřít ze správy zdrojového kódu** :

![Zvýrazněné tlačítko Přidat pro přidání nového serveru do seznamu](media/tfvc-add-new-server.png)

V seznamu vyberte poskytovatele a zadejte své přihlašovací údaje:

![Dialogové okno zobrazující možnost pro poskytovatele správy zdrojového kódu](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Vytváří se nový pracovní prostor.

Chcete-li začít pracovat s projektem, je nutné mít _pracovní prostor_. Pokud ještě nemáte pracovní prostor, můžete ho vytvořit v dialogovém okně **Otevřít ze správy zdrojového kódu** v **pracovním prostoru** .

![Vytvořit nový pracovní prostor – možnost ComboBox](media/tfvc-create-new-workspace.png)

Nastavte název a místní cestu k novému pracovnímu prostoru a vyberte **vytvořit pracovní prostor**:

![Zadání názvu a místní cesty k novému pracovnímu prostoru](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Použití Průzkumníka zdrojového kódu

Po vytvoření pracovního prostoru a namapování projektu můžete začít pracovat s _průzkumníkem zdrojového kódu_.

Chcete-li otevřít Průzkumníka zdrojového kódu, vyberte možnost Správa **verzí > TFS/Azure DevOps > Průzkumník správy zdrojových souborů** položka nabídky.

Průzkumník zdrojového kódu umožňuje procházet všechny mapované projekty, jejich soubory a složky. Umožňuje také provádět všechny základní akce správy zdrojového kódu, jako jsou:

- Získat nejnovější verzi
- Získat konkrétní verzi
- Rezervace souborů a vrácení souborů se změnami
- Zamknout a odemknout soubory
- Přidávání, odstraňování a přejmenování souborů
- Zobrazit historii
- Porovnejte změny.

Mnohé z těchto akcí jsou k dispozici prostřednictvím akcí kontextu v projektu:

![Akce místní nabídky pro projekt](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Správa pracovních prostorů

Pokud jste ještě nevytvořili pracovní prostor, jak je popsáno v části [Vytvoření pracovního prostoru](#creating-a-new-workspace) , Všimněte si, že je Průzkumník zdrojového kódu prázdný:

![prázdný Průzkumník zdrojového kódu](media/tfvc-setup-empty-sce.png)

Chcete-li nastavit vzdálený projekt pomocí místního pracovního prostoru, použijte následující postup:

1. V poli se seznamem vyberte **Server** .
1. Všimněte si, že nejsou k dispozici žádné pracovní prostory a že místní cesta není namapovaná. Vyberte odkaz **není mapováno** k zobrazení dialogového okna **vytvořit nový pracovní prostor** .
1. Zadejte název pracovního prostoru a potom klikněte na **Přidat pracovní složku** pro mapování projektu do místní složky v počítači:

    ![Dialog vytvořit nový pracovní prostor se zobrazenými výchozími možnostmi](media/tfvc-workspace1.png)

1. Vyberte složku $, abyste namapovali všechny projekty na vašem serveru do stejného pracovního prostoru, nebo vyberte jednotlivý projekt a klikněte na **OK**:

    ![Dialog vyhledat složku zobrazující všechny projekty](media/tfvc-workspace2.png)

1. Vyberte umístění na místním počítači, na který chcete namapovat projekt, a klikněte na **Vybrat složku**.
1. Kliknutím na **OK** potvrďte podrobnosti nového pracovního prostoru.

    ![Dialog vytvořit nový pracovní prostor s přidanou pracovní složkou](media/tfvc-workspace3.png)

Po nastavení pracovního prostoru ho můžete změnit nebo odebrat kliknutím na tlačítko **spravovat pracovní prostory** v Průzkumníkovi zdrojového kódu.

![Správa pracovních prostorů](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Odstraňování potíží a známé problémy

#### <a name="problems-using-basic-authentication"></a>Problémy s použitím základního ověřování

K ověření pomocí serveru můžete použít následující možnosti:

- OAuth
- Základní
- NTLM

Pokud chcete použít základní ověřování, je nutné povolit **alternativní přihlašovací údaje pro ověřování** v Azure DevOps Services, a to pomocí následujících kroků:

1. Přihlaste se ke svojí organizaci Azure DevOps jako vlastník (https:\//dev.Azure.com/{Organization}/{Project}).

2. Na panelu nástrojů organizace vyberte ikonu ozubeného kolečka a vyberte **zásady**:

    ![Vybraná možnost nastavení zásad](media/tfvc-auth2.png)

3. Zkontrolujte nastavení připojení aplikace. Tato nastavení změňte na základě zásad zabezpečení:

    ![Vybraná možnost nastavení zásad](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>V TFVC se mi nezobrazuje žádný

Chcete-li nastavit Správa verzí Team Foundation (TFVC) ve vývojovém počítači, je **třeba** vytvořit pracovní prostor, jak je popsáno v části [Správa pracovních prostorů](#managing-workspaces) .

V Průzkumník správy zdrojových souborů stiskněte tlačítko **spravovat pracovní prostory** . Postupujte podle kroků pro namapování projektu na složku ve vývojovém počítači.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Nezobrazují se žádné/všechny moje projekty

Po ověření by se měl zobrazit seznam projektů. Ve výchozím nastavení jsou zobrazeny pouze projekty TFS. Chcete-li zobrazit další typy projektů, zaškrtněte políčko Zobrazit všechny projekty.

Mějte na paměti, že pokud nemáte správná oprávnění, projekty, které se nacházejí na serveru, se nezobrazí.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Zobrazuje se chyba "nelze vytvořit pracovní prostor". Zkuste to prosím znovu.

Když se pokoušíte [vytvořit nový pracovní prostor](#creating-a-new-workspace), měli byste se ujistit, že jsou splněné následující podmínky:

- V názvu pracovního prostoru není žádné použití neplatných znaků.
- Název musí být kratší než 64 znaků.
- Místní cestu nemohou použít žádné jiné pracovní prostory.

### <a name="see-also"></a>Viz také:

- [Vývoj a sdílení kódu v TFVC pomocí sady Visual Studio (ve Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)