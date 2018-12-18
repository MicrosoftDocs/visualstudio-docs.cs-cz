---
title: Team Foundation Version Control (TFVC)
description: Připojení k serveru Team Foundation Server nebo služby Azure DevOps s Team Foundation Version Control (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 9cb6a466d764c85012477fb2d849c05920908f02
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295927"
---
# <a name="connecting-to-team-foundation-version-control"></a>Připojování k Team Foundation – správa verzí

> [!NOTE]
> Podpora Team Foundation – správa verzí je aktuálně ve verzi preview a některé funkce není dosud plně funkční. Jsme rádi, zpětnou vazbu od vás na všechny problémy na [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/41/index.html). Další změny jsou stále chystá!

Úložiště Azure poskytuje dva modely správy verzí: Git, který je distribuován správy verzí a Team Foundation verze ovládacího prvku (TFVC), což je centralizovaná správa verzí. Tento článek obsahuje přehled a výchozí bod pro TFVC pomocí sady Visual Studio pro Mac.

## <a name="requirements"></a>Požadavky

* Visual Studio Community, Professional nebo Enterprise for Mac verze 7.5 nebo novější.
* Služby Azure DevOps, nebo Team Foundation Server 2013 a novější.
* Projekt Azure DevOps Services nebo Team Foundation Server nakonfigurován pro použití správy verzí Team Foundation.

## <a name="installation"></a>Instalace

V sadě Visual Studio pro Mac, zvolte **sady Visual Studio > rozšíření** z nabídky. V **Galerie** kartu, vyberte možnost **verzí > správy verzí Team Foundation serveru TFS a VSTS** a klikněte na tlačítko **nainstalovat**:

![Správce rozšíření](media/tfvc-install.png)

Postupujte podle pokynů k instalaci rozšíření. Po instalaci ji restartujte integrované vývojové prostředí.

## <a name="updating-the-extension"></a>Aktualizuje se rozšíření

Aktualizace rozšíření TFVC probíhají pravidelně. Přístup k aktualizace, zvolte **sady Visual Studio > rozšíření...**  z nabídky a vybereme **aktualizace** kartu. Vyberte požadované rozšíření v seznamu a stisknutím klávesy **aktualizace** tlačítka:

![Aktualizace zobrazení Správce rozšíření](media/tfvc-update.png)

Stisknutím klávesy **nainstalovat** v dalším dialogovém okně starý balíček odinstalovat a nainstalovat nové.

Informace o tom, co je nového v jednotlivých verzích, najdete v článku [poznámky k verzi](/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes).

## <a name="using-the-add-in"></a>Pomocí doplňku

Po instalaci rozšíření, vyberte **verzí > TFS/Azure DevOps > Otevřít ze vzdáleného úložiště** položky nabídky.

![Položka nabídky otevřít rozšíření](media/tfvc-source-control-explorer-devops.png)

Zvolte buď VSTS nebo Team Foundation Server, a začít pracovat se stisknutím klávesy **pokračovat**:

![Připojení k serveru](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Ověřování Azure úložišť

Když vyberete projekt, který je hostitelem úložiště Azure, budete vyzváni k zadání podrobnosti o vašem účtu Microsoft:

![Spojte se s Azure úložišť](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>Ověřování serveru TFS

Pro připojení k TFS, zadejte podrobnosti o serveru a přihlašovací údaje účtu. Zadejte doménu na použití ověřování NTLM, jinak nechejte pole prázdné, použije se základní ověřování. Vyberte **přidat Server**:

![Přihlaste se k serveru TFS](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Výběr projektu

Jakmile byli jste úspěšně ověřeni, zobrazí se seznam úložišť, které jsou přidružené k účtu v **otevřít ze správy zdrojových kódů** dialogové okno:

![Otevřít ze správy zdrojových kódů dialogové okno s projekty, zobrazí](media/tfvc-vsts-projects.png)

Toto dialogové okno je uspořádaný s následující uzly:

- Azure DevOps organizace nebo kolekci – zobrazí se všechny organizace, které jsou připojené k účtu Microsoft, který jste přihlášení.
- Projekty – v každé organizaci nebo kolekci, může mít celou řadou projektů. Projekt je, kde jsou hostované zdrojový kód, pracovní položky a automatizované sestavování.

V tomto okamžiku můžete vyhledávat a filtrovat podle názvu projektu nebo organizace.

### <a name="adding-a-new-server"></a>Přidání nového serveru

Chcete-li přidat nový server do seznamu, stiskněte **přidat hostitele** tlačítko **otevřít ze správy zdrojových kódů** dialogové okno:

![Zvýrazní tlačítko pro přidání nového serveru do seznamu přidat](media/tfvc-add-new-server.png)

Vyberte poskytovatele ze seznamu a zadejte svoje přihlašovací údaje:

![Dialogové okno zobrazující možnost pro poskytovatele správy zdrojového kódu](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>Vytváří se nový pracovní prostor

Pokud chcete začít pracovat s projektem, budete muset mít _pracovní prostor_. Pokud ještě nemáte pracovní prostor, můžete vytvořit jeden z **pracovní prostor** – pole se seznamem v **otevřít ze správy zdrojových kódů** dialogové okno:

![Vytvořit nový pracovní prostor – pole se seznamem možností](media/tfvc-create-new-workspace.png)

Nastavte název a místní cestu k novému pracovnímu prostoru a vyberte **vytvořit pracovní prostor**:

![Zadat místní cestu a název nového pracovního prostoru](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Pomocí Průzkumníka zdrojového kódu

Po vytvoření pracovního prostoru a mapována do projektu, můžete začít pracovat s _Průzkumník zdrojového kódu_.

Otevřít Průzkumníka zdrojového kódu, vyberte **verzí > TFS/Azure DevOps > Průzkumník správy zdrojového kódu** položky nabídky.

Průzkumník zdrojového kódu umožňuje procházet z namapované projekty, jejich soubory a složky. Také umožňuje provádět všechny akce správy základní zdrojů, jako:

- Získat nejnovější verzi
- Získání určité verze
- Rezervace souborů a vrácení souborů se změnami
- Zamknutí a odemknutí soubory
- Přidání, odstranění a přejmenování souborů
- Zobrazit historii
- Porovnejte změny.

Mnohé z těchto akcí jsou k dispozici prostřednictvím kontextu akce na projekt:

![Místní nabídka Akce pro projekt](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Správa pracovních prostorů

Pokud jste ještě nevytvořili pracovního prostoru, jak je popsáno v [vytvoření pracovního prostoru](#creating-a-new-workspace) oddílu, můžete si všimnout, že je prázdný Průzkumník zdrojového kódu:

![prázdný zdrojový kód explorer](media/tfvc-setup-empty-sce.png)

Nastavení vzdáleného projekt pomocí místního pracovního prostoru, postupujte následovně:

1. Vyberte **Server** z pole se seznamem.
1. Mějte na paměti, že neexistují "žádné pracovní prostory" a zda je místní cesta "Nenamapované". Vyberte **nenamapované** odkazu zobrazíte **vytvořit nový pracovní prostor** dialogového okna.
1. Zadejte název pracovního prostoru a potom klikněte na tlačítko **pracovní složka** mapování projektu do místní složky v počítači:

    ![Vytvořit nový pracovní prostor dialog s informací, výchozí možnosti](media/tfvc-workspace1.png)

1. Vyberte složky "$" do všech projektů na serveru mapují na stejný pracovní prostor, nebo vyberte jednotlivé projekt a klikněte na tlačítko **OK**:

    ![Procházet pro složku dialogové okno zobrazující všechny projekty](media/tfvc-workspace2.png)

1. Vyberte umístění na místním počítači, který chcete namapovat projekt(y) na tento a klikněte na tlačítko **vybrat složku**.
1. Zkontrolujte podrobnosti o nový pracovní prostor stisknutím kombinace kláves **OK**

    ![Vytvořit dialogové okno Nový pracovní prostor se přidá pracovní složky](media/tfvc-workspace3.png)

Po nastavení pracovního prostoru lze změnit nebo odebrat po kliknutí **spravovat pracovní prostory** tlačítko v Průzkumníku zdrojového kódu.

![Správa pracovních prostorů](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Poradce při potížích

### <a name="problems-using-basic-authentication"></a>Potíže při použití základního ověřování

Tyto možnosti lze použít k ověření serveru:

- OAuth
- Základní
- NTLM

Základní ověřování je nutná pro povolení **přihlašovací údaje pro alternativní ověření** ve službách Azure DevOps, pomocí následujících kroků:

1. Přihlaste se k vaší organizaci Azure DevOps jako vlastník (https://dev.azure.com/{organization}/{project}).

2. Z panelu nástrojů organizace, vyberte ikonu ozubeného kola a vyberte **zásady**:

    ![Vybraná možnost nastavení zásad](media/tfvc-auth2.png)

3. Zkontrolujte nastavení připojení k aplikaci. Změna těchto nastavení v závislosti na vašich zásadách zabezpečení:

    ![Vybraná možnost nastavení zásad](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>Nevidím v TFVC nic

Nastavit si Team Foundation verze ovládacího prvku (TFVC) ve vašem vývojovém počítači můžete **musí** vytvořit pracovní prostor, jak je popsáno v [Správa pracovních prostorů](#managing-workspaces) oddílu.

V Průzkumníku správy zdrojového kódu, stiskněte **spravovat pracovní prostory** tlačítko. Postupujte podle kroků pro mapování projektu do složky na svém vývojovém počítači.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Nevidím žádné / all Moje projekty

Po ověření, měli byste vidět seznam projektů. Ve výchozím nastavení jsou uvedeny pouze projekty TFS. Pokud chcete zobrazit jiné typy projektů, zaškrtněte políčko "«Zobrazit všechny projekty".

Mějte na paměti, že projekty, které jsou na serveru se nezobrazí, pokud nemáte dostatečná oprávnění.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Dochází k chybě "nejde vytvořit pracovní prostor. Zkuste to prosím znovu"

Při pokusu o [vytvořit nový pracovní prostor](#creating-a-new-workspace), se ujistěte, že jsou splněny následující podmínky:

- Zákaz použití neplatné znaky v názvu pracovního prostoru.
- Název musí být menší než 64 znaků.
- Místní cesta nemůže využívat ostatní pracovní prostory.

## <a name="see-also"></a>Viz také:

- [Vývoj a sdílení kódu v TFVC pomocí sady Visual Studio (Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)