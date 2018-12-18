---
title: Nastavení úložiště Subversion
description: Pomocí dílčích verzí v sadě Visual Studio pro Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 3995db4ef4609f68512dede454855da1f770141f
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295550"
---
# <a name="set-up-a-subversion-repository"></a>Nastavení úložiště Subversion

Subversion je centralizovaná _systém správy verzí_, což znamená, že je jeden server, který obsahuje všechny soubory a revize, kteří uživatelé sjednotit, zkontrolujte všechny verze všech souborů. Když soubory jsou rezervovány ze vzdáleného úložiště Subversion, uživatel získá snímek úložiště v tomto okamžiku v čase.

Pro účely vaší verzí Subversion, musíte nainstalovat na svém počítači. A zkontrolujte, zda se dílčí verze je nainstalována váš počítač, v terminálu zadejte následující příkaz:

```bash
svn --version
```

Tento příkaz vrátí číslo verze.

Pokud ještě nemáte nainstalovaný Subversion, po instalaci je nejjednodušší způsob, jak ho získat _příkazového řádku nástroje Xcode_. Pomocí následujícího příkazu nainstalujte nástroje příkazového řádku Xcode a Subversion.

```bash
xcode-select --install
```

Jakmile dílčí verze je nainstalovaná na počítači, použijte následující kroky před publikováním projektu v SVN.

1. Vytvořte online volného úložiště SVN. V tomto příkladu [Assembla](https://app.assembla.com/) byl použit. Po vytvoření adresy URL, poskytneme vám, který se použije pro připojení k úložišti:

    ![Zkopírujte adresu URL SVN](media/version-control-subversion1-sml.png)

2. Otevření nebo vytvoření sady Visual Studio pro Mac projektu.

3. Klikněte pravým tlačítkem myši na projekt a vyberte **verzí > Publikovat ve správě verzí...** :

    ![Spustit publikování projektu](media/version-control-subversion2.png)

4. V **připojit k úložišti** kartu, vyberte možnost **Subversion** shora rozevíracího seznamu.

5. Zadejte adresu URL z kroku 1. Po zadání adresy URL v ostatních polích se vyplní ve výchozím nastavení:

    ![Vybrat úložiště a zadejte podrobnosti dialogového okna](media/version-control-subversion3.png)

7. Klikněte na tlačítko **OK** a pak to potvrďte klepnutím **publikovat**.

7. Pokud se zobrazí výzva, zadejte svoje přihlašovací údaje pro lokality, na kterém jste vytvořili úložiště, jak je znázorněno níže:

    ![Zadání přihlašovacích údajů úložiště subversion](media/version-control-subversion5.png)

8.  Všechny příkazy správy verzí k dispozici, teď by se zobrazovat v nabídce Řízení verze.

## <a name="see-also"></a>Viz také:

- [Práce s úložištěm Subversion](working-with-subversion.md)