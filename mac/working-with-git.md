---
title: Práce s úložištěm Git
description: Použití Gitu ve Visual Studiu pro Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 767c08505877391d71ca085097a0464d516f4f24
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "70108027"
---
# <a name="working-with-git"></a>Práce s úložištěm Git

Git je distribuovaný systém správy verzí, který umožňuje týmům pracovat na stejných dokumentech současně. To znamená, že existuje centrální server, který obsahuje všechny soubory, ale když je úložiště rezervováno z tohoto centrálního zdroje, celé úložiště je klonováno do místního počítače.

V následujících částech se bude zkoumat, jak se Git dá použít pro správu verzí ve Visual Studiu for Mac.

## <a name="git-version-control-menu"></a>Nabídka řízení verzí Gitu

Obrázek níže znázorňuje možnosti poskytované Visual Studio pro Mac položkou nabídky Správa verzí:

![Položka nabídky Správa verzí](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Zatlačte a táhněte

Tlačení a tahání jsou dvě nejčastěji používané akce v rámci Gitu. Chcete-li synchronizovat změny provedené jinými uživateli ve vzdáleném úložišti, je nutné jej **stáhnout.** To se provádí ve Visual Studiu pro Mac výběrem **správy verzí > aktualizačního řešení**.

Jakmile soubory aktualizujete, zkontrolujete a posuzujete, musíte je **zasunout** do vzdáleného úložiště, aby ostatní měli přístup k vašim změnám. To se provádí ve Visual Studiu pro Mac výběrem **správy verzí > push změny**. Zobrazí se dialogové okno Push, které umožňuje zobrazit potvrzené změny, a vyberte větev, na kterou chcete tlačit:

![Dialogové okno zobrazující větev, do které chcete potvrdit](media/version-control-gitPush.png)

Změny můžete potvrdit a posunout současně prostřednictvím dialogového okna Potvrdit:

![Možnost zobrazující, jak potvrdit a tlačit současně.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Vina, protokol a sloučení

V dolní části okna je zobrazeno pět karet, jak je znázorněno níže:

![Karty Správa verzí](media/version-control-gitTabs.png)

Ty umožňují následující akce:

* **Zdroj** - Zobrazí soubor zdrojového kódu.
* **Změny** - Zobrazí změnu kódu mezi místním a základním souborem. Můžete také porovnat různé verze souboru z různých hodnot hashe:

    ![Karta Změny](media/version-control-gitChange.png)

* **Blame** - Zobrazí uživatelské jméno uživatele přidruženého ke každé části kódu.
* **Protokol** – Zobrazí všechny revize, časy, data, zprávy a uživatele, kteří jsou zodpovědní za soubor:

    ![Karta Protokol](media/version-control-gitLog.png)

* **Sloučení** - To lze použít, pokud máte konflikt sloučení při potvrzení práce. Zobrazuje vizuální reprezentaci změn provedených vámi a ostatním vývojářem, což umožňuje čistě kombinovat obě části kódu.

## <a name="switching-branches"></a>Přepínání větví

Ve výchozím nastavení se první větev vytvořená v úložišti označuje jako **Hlavní** větev. Není technicky nic jiného mezi hlavní větev a jakékoli jiné, ale hlavní větev je ten, který je nejčastěji myšlenka ve vývojových týmech jako 'live' nebo 'výroba' pobočka.

Samostatnou linii vývoje lze vytvořit větvením mimo Master (nebo jakoukoli jinou větev, když na to přijde). To poskytuje novou verzi hlavní větve v určitém okamžiku, což umožňuje vývoj nezávisle na tom, co je "živé". Použití větví tímto způsobem se často používá pro funkce při vývoji softwaru

Uživatelé mohou vytvořit libovolný počet větví pro každé úložiště, ale doporučuje se, aby po dokončení používání větve byla odstraněna, aby bylo úložiště uspořádáno.

Pobočky se v sadě Visual Studio for Mac zobrazí procházením **aplikace Správa verzí > Správa větví a dálkových ovladačů...**:

![Zobrazení poboček](media/version-control-gitBranch2.png)

Přepněte do jiné větve tak, že ji vyberete v seznamu a stisknete tlačítko **Přepnout na větev.**

Chcete-li vytvořit novou větev, vyberte tlačítko **Nový** v dialogovém okně konfigurace úložiště Git. Zadejte nový název větve:

![Vytvořit novou větev](media/version-control-gitBranch.png)

Můžete také nastavit vzdálenou větev do _větví sledování._ Další informace o sledování větví načapěnou v [dokumentaci k Gitu](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Podívejte se na aktuální větev v panelu řešení vedle názvu projektu:

 ![Aktuální větev zobrazená v panelu řešení](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Revize a potvrzení

Chcete-li zkontrolovat změny v souborech, použijte karty Změny, Navit, Protokol a Sloučit v každém dokumentu, ilustrované dříve v tomto tématu.

Zkontrolujte všechny změny v projektu procházením **položky nabídky Správa verzí > Revizní řešení a Potvrdit:**

![Zkontrolovat zobrazení kódu](media/version-control-gitReviewCommit.png)

To umožňuje zobrazit všechny změny v každém souboru projektu s možností vrátit, vytvořit opravu nebo potvrdit.

Chcete-li potvrdit soubor do vzdáleného úložiště, stiskněte **potvrzení**, zadejte zprávu o potvrzení a potvrďte tlačítkem Potvrzení:

![Potvrzení souboru](media/version-control-gitCommit.png)

Jakmile změny podáte, zatlačte je do vzdáleného úložiště, aby je ostatní uživatelé mohli zobrazit.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Viz také

* [Sdílení kódu s Visual Studio 2017 a Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)
