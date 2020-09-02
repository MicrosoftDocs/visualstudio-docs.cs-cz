---
title: Instalace a Správa místního obsahu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 569254c9df668c7755116f37a819fe65a3ecaa59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670464"
---
# <a name="install-and-manage-local-content"></a>Instalace a správa místního obsahu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí Microsoft Help Viewer můžete přidat, odebrat, aktualizovat a přesunout obsah aplikace, který je nainstalovaný v počítači, aby vyhovoval potřebám vývoje softwaru.

 Chcete-li spravovat obsah v místním počítači, je nutné se přihlásit pomocí účtu, který má oprávnění správce. Kromě toho nemusí být možné spravovat místní obsah, pokud pracujete v podnikovém prostředí, protože správci systému můžou tato rozhodnutí udělat pro vaši organizaci. Další informace najdete v příručce pro [správce aplikace Help Viewer](../ide/help-viewer-administrator-guide.md).

## <a name="changing-the-content-installation-source"></a>Změna zdroje instalace obsahu
 Ve výchozím nastavení aplikace Help Viewer nainstaluje obsah pomocí online služby Microsoftu jako zdroje. Obecně byste neměli měnit zdroj obsahu, pokud nepracujete v podnikovém prostředí, pro které správce systému již nainstaloval obsah do jiného umístění.

#### <a name="to-change-the-content-installation-source"></a>Změna zdroje instalace obsahu

1. Na kartě **Spravovat obsah** klikněte na tlačítko možnosti **disku** .

    > [!NOTE]
    > Možnost **disk** nebude k dispozici, pokud vám správce zabrání v úpravách zdroje instalace obsahu. Další informace najdete v příručce pro [správce aplikace Help Viewer](../ide/help-viewer-administrator-guide.md).

2. Proveďte jeden z následujících kroků:

    - Zadejte cestu k souboru. msha nebo adresu URL koncového bodu služby.

    - Klikněte na tlačítko Procházet (**...**) a přejděte k souboru. msha.

    - V seznamu vyberte položku, která se naposledy používala.

## <a name="download-and-install-content-locally"></a>Stažení a instalace obsahu místně
 Pokud stahujete a instalujete obsah do místního počítače, můžete zobrazit témata bez připojení k Internetu.

> [!IMPORTANT]
> Chcete-li nainstalovat obsah, je nutné se přihlásit pomocí účtu, který má oprávnění správce.

 Pokud je integrované vývojové prostředí (IDE) sady Visual Studio nastaveno na jiný jazyk než angličtinu, můžete nainstalovat obsah v angličtině, lokalizovaný obsah nebo obojí. Pokud však nainstalujete pouze anglickou verzi a zaškrtávací políčko **Zahrnout obsah v angličtině do všech navigačních karet a požadavků F1** v dialogovém okně **Možnosti prohlížeče** není zaškrtnuto, zobrazí se žádný obsah.

#### <a name="to-download-and-install-content"></a>Stažení a instalace obsahu

1. Klikněte na kartu **Spravovat obsah** .

2. V seznamu obsah klikněte na odkaz **Přidat** vedle knihy nebo knihy, které chcete stáhnout a nainstalovat.

     Kniha je přidána do seznamu **nedokončené změny** a odhadovaná velikost knihy nebo knih, které jste zadali, se zobrazí pod seznamem. Vzhledem k tomu, že některé knihy sdílejí témata, může být celková velikost stahovaných více knih menší než výsledek přidávání velikostí každé knihy, kterou jste zadali.

3. Klikněte na tlačítko **aktualizovat** .

     Knihy nebo knihy, které jste zadali, se nainstalují spolu s aktualizacemi pro knihy, které už máte ve svém počítači. Doba instalace se liší, ale průběh můžete zobrazit ve stavovém řádku.

## <a name="removing-local-content"></a>Odebírání místního obsahu
 Odstraněním nežádoucího obsahu z počítače můžete ušetřit místo na disku.

> [!IMPORTANT]
> Chcete-li odebrat obsah, je nutné mít oprávnění správce.

 Pokud je prostředí Visual Studio IDE nastaveno na jiný jazyk než angličtinu, nebude zobrazen žádný obsah. v dialogovém okně **Možnosti prohlížeče** je zaškrtnuto políčko **Zahrnout anglický obsah do všech navigačních karet a požadavků F1** .

#### <a name="to-remove-content"></a>Postup odebrání obsahu

1. Klikněte na kartu **Spravovat obsah** .

2. V seznamu obsah klikněte na odkaz **Odebrat** vedle knihy nebo knih, které chcete odebrat.

     Kniha je přidána do seznamu **nedokončené změny** .

3. Klikněte na tlačítko **aktualizovat** .

     Knihy nebo knihy, které jste zadali, se z počítače odeberou.

## <a name="updating-local-content"></a>Aktualizace místního obsahu
 Stavový řádek označuje, že jsou k dispozici aktualizace k nainstalovanému obsahu.

> [!IMPORTANT]
> Pokud chcete, aby aplikace Help Viewer automaticky kontrolovala aktualizace online, je nutné otevřít dialogové okno **Možnosti prohlížeče** a pak zaškrtnout políčko **Přejít do režimu online a vyhledat aktualizace obsahu** .

#### <a name="to-update-local-content"></a>Aktualizace místního obsahu

- V pravém dolním rohu stavového řádku vyberte odkaz **klikněte sem a Stáhněte si hned** .

  Doba aktualizace se může lišit, ale průběh aktualizace můžete zobrazit ve stavovém řádku.

## <a name="moving-local-content"></a>Přesunutí místního obsahu
 Přesunutím nainstalovaného obsahu z místního počítače do sdílené síťové složky nebo do jiného oddílu v místním počítači můžete ušetřit místo na disku.

> [!IMPORTANT]
> Chcete-li přesunout obsah, je nutné se přihlásit pomocí účtu, který má oprávnění správce.

#### <a name="to-move-local-content"></a>Přesunutí místního obsahu

1. Na kartě **Spravovat obsah** klikněte na tlačítko **přesunout** v části **cesta k místnímu úložišti**.

     Otevře se dialogové okno **přesunout obsah** .

2. Do textového pole **do** zadejte jiné umístění pro obsah a pak klikněte na tlačítko **OK** .

3. Po přesunutí obsahu klikněte na tlačítko **Zavřít** .

## <a name="see-also"></a>Viz také
 [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)
