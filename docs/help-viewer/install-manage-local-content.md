---
title: Nainstalovat dokumentaci místní nápovědy
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer]
- updating local content [Help Viewer]
- Help Viewer, content installation source
- Help Viewer, updating local content
- Help Viewer, changing content installation source
- installing local content [Help Viewer]
- content installation source [Help Viewer]
- downloading content [Help Viewer]
- removing local content [Help Viewer]
- Help Viewer, removing local content
- Help Viewer, installing local content
- Help Viewer, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fab06fee0dadd28d6b8feb793d29fb1e22e0b00b
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378137"
---
# <a name="install-and-manage-local-content"></a>Instalace a Správa místního obsahu

Pomocí Microsoft Help Viewer můžete přidat, odebrat, aktualizovat a přesunout obsah nápovědy, který je nainstalován v počítači podle vašich potřeb vývoje softwaru.

Pokud chcete spravovat obsah v místním počítači, musí se přihlásit pomocí účtu, který má oprávnění správce. Kromě toho nemusí být schopné spravovat místní obsah, pokud pracujete v podnikovém prostředí, protože správci systému mohou tyto rozhodování pro vaši organizaci. Další informace najdete v tématu [Příručka pro správce aplikace Help Viewer](../help-viewer/administrator-guide.md).

## <a name="change-the-content-installation-source"></a>Změna zdroje instalace obsahu

Ve výchozím nastavení nainstaluje Help Viewer obsah s využitím online službu Microsoftu jako zdroj. Byste obvykle neměli měnit zdroj obsahu Pokud pracujete v podnikovém prostředí, u kterého správce systému již nainstaloval obsah do jiného umístění.

### <a name="to-change-the-content-installation-source"></a>Změna zdroje instalace obsahu

1.  Na **spravovat obsah** , vyberte **disku** přepínač.

    > [!NOTE]
    > **Disku** možnost není k dispozici v případě, že správce má že nesmíte měnit zdroj instalace obsahu. Další informace najdete v tématu [Příručka pro správce aplikace Help Viewer](../help-viewer/administrator-guide.md).

2.  Proveďte jeden z následujících kroků:

    -   Zadejte cestu *.msha* soubor nebo adresa URL koncového bodu služby.

    -   Klikněte na tlačítko procházení (**...** ) tlačítko Přejít na *.msha* souboru.

    -   V seznamu vyberte položku, která byla naposledy použita.

## <a name="download-and-install-content-locally"></a>Stažení a instalace obsahu místně

Pokud stáhnete a nainstalujete obsah v místním počítači, můžete zobrazit témata, pokud nemáte připojení k Internetu.

> [!IMPORTANT]
> Pokud chcete nainstalovat obsah, musí se přihlásit pomocí účtu, který má oprávnění správce.

> [!NOTE]
> Pokud integrované vývojové prostředí sady Visual Studio je nastaven na jiný jazyk než angličtinu, můžete nainstalovat obsah v angličtině, lokalizovaný obsah nebo obojí. Ale žádný obsah se zobrazí v případě, že nainstalujete pouze anglickou verzi a **ve všech navigačních karet a žádostí F1 zahrnout anglický obsah** zaškrtávací políčko **možnosti prohlížeče** dialogové okno se vymaže.

### <a name="to-download-and-install-content"></a>Ke stažení a nainstalování obsahu

1.  Zvolte **spravovat obsah** kartu.

2.  V seznamu obsahu zvolte **přidat** odkaz vedle knih, které chcete stáhnout a nainstalovat.

     Kniha je přidána do **čekající změny** seznamu a odhadovaná velikost knih, které jste zadali, se zobrazí pod tímto seznamem. Vzhledem k tomu, že některé knihy témata sdílejí, může být celková stahovaná velikost při několika knih menší než výsledek sečtením velikosti jednotlivé knihy, které jste zadali.

3.  Zvolte **aktualizace** tlačítko.

     Knihy, které jste zadali, jsou nainstalovány společně se všemi aktualizacemi pro knihy, které už máte ve vašem počítači. Časy instalace lišit, ale můžete zobrazit průběh ve stavovém řádku.

## <a name="remove-local-content"></a>Odebrání lokálního obsahu

Odstraněním nežádoucího obsahu z počítače můžete ušetřit místo na disku.

> [!IMPORTANT]
> Musíte mít oprávnění správce k odebrání obsahu.

> [!NOTE]
> Žádný obsah se zobrazí, pokud integrovaném vývojovém prostředí sady Visual Studio je nastaven na jiný jazyk než angličtinu, odeberete lokalizovaný obsah a **ve všech záložkách a žádostí F1 zahrnout anglický obsah** zaškrtávací políčko **možnosti prohlížeče** dialogové okno se vymaže.

### <a name="to-remove-content"></a>Chcete-li odebrat obsah

1.  Zvolte **spravovat obsah** kartu.

2.  V seznamu obsahu zvolte **odebrat** odkaz vedle knih, které chcete odebrat.

     Kniha je přidána do **čekající změny** seznamu.

3.  Zvolte **aktualizace** tlačítko.

     Knihy, které jste zadali, se odeberou z vašeho počítače.

## <a name="update-local-content"></a>Aktualizace místního obsahu

Stavový řádek označuje, kdy jsou k dispozici aktualizace nainstalovaného obsahu.

> [!IMPORTANT]
> Pokud chcete, aby **aplikace Help Viewer** k automaticky vyhledávala online aktualizace, je nutné otevřít **možnosti prohlížeče** dialogové okno a potom vyberte **přejít online pro kontrolu aktualizací obsahu**zaškrtávací políčko.

### <a name="to-update-local-content"></a>Aktualizace místního obsahu

- V pravém dolním rohu stavového řádku, vyberte **pro stažení klikněte zde** odkaz.

Doba aktualizace se může lišit, ale můžete ve stavovém řádku zobrazit průběh aktualizace.

## <a name="move-local-content"></a>Přesunutí místního obsahu

Přesunutím nainstalovaného obsahu z místního počítače do sdílené síťové složky nebo na jiný oddíl v místním počítači můžete ušetřit místo na disku.

> [!IMPORTANT]
> Abyste mohli přesouvat obsah, musí se přihlásit pomocí účtu, který má oprávnění správce.

### <a name="to-move-local-content"></a>Přesunutí místního obsahu

1.  Na **spravovat obsah** , vyberte **přesunout** tlačítko **místní cesta Store**.

     **Přesunout obsah** zobrazí se dialogové okno.

2.  V **k** textového pole zadejte jiné umístění pro obsah a klikněte na tlačítko **OK** tlačítko.

3.  Zvolte **Zavřít** tlačítko obsah byl přesunut.

## <a name="see-also"></a>Viz také:

- [Microsoft Help Viewer 2.2](../help-viewer/overview.md)