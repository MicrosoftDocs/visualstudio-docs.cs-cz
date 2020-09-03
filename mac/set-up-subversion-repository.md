---
title: Nastavení úložiště Subversion
description: Použití podverze v Visual Studio pro Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.topic: how-to
ms.openlocfilehash: 78a5dd2abbef177e2eb949d25d779a46ecc65bda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950689"
---
# <a name="set-up-a-subversion-repository"></a>Nastavení úložiště podverze

Podverze je centralizovaný _systém správy verzí_, což znamená, že existuje jeden server, který obsahuje všechny soubory a revize, ze kterých mohou uživatelé rezervovat jakoukoli verzi libovolného souboru. Když jsou soubory rezervovány ze vzdáleného úložiště podverze, uživatel získá snímek úložiště v daném časovém okamžiku.

Chcete-li použít podverzi správy verzí, je nutné ji nainstalovat do počítače. Pokud chcete zjistit, jestli je v počítači nainstalovaná dílčí verze, použijte v terminálu tento příkaz:

```bash
svn --version
```

Tento příkaz vrátí číslo verze.

Pokud není podverze ještě nainstalovaná, nejjednodušší způsob, jak ji získat, je nainstalovat _nástroje příkazového řádku Xcode_. Pomocí následujícího příkazu nainstalujte nástroje příkazového řádku Xcode a dílčí verzi.

```bash
xcode-select --install
```

Po instalaci dílčí verze na váš počítač použijte následující postup k publikování projektu v SVN.

1. Vytvořte bezplatné úložiště SVN online. V tomto příkladu se použil [Assembla](https://app.assembla.com/) . Po vytvoření se poskytne adresa URL, která se použije pro připojení k úložišti:

    ![zkopírovat adresu URL SVN](media/version-control-subversion1-sml.png)

2. Otevřete nebo vytvořte projekt Visual Studio pro Mac.

3. Klikněte pravým tlačítkem na projekt a vyberte možnost Správa **verzí > publikovat ve správě verzí...**:

    ![Spustit publikování projektu](media/version-control-subversion2.png)

4. Na kartě **připojit k úložišti** vyberte v horním rozevíracím seznamu **podverzi** .

5. Zadejte adresu URL z kroku 1. Po zadání adresy URL se ve výchozím nastavení vyplní ostatní pole:

    ![Výběr úložiště a zadání podrobností – dialogové okno](media/version-control-subversion3.png)

7. Klikněte na **OK** a potvrďte stisknutím tlačítka **publikovat**.

7. Pokud se zobrazí výzva, zadejte přihlašovací údaje pro web, na kterém jste úložiště vytvořili, jak je znázorněno níže:

    ![Zadání přihlašovacích údajů pro úložiště podverze](media/version-control-subversion5.png)

8. Všechny dostupné příkazy správy verzí by nyní měly být viditelné v nabídce správy verzí.

## <a name="see-also"></a>Viz také

- [Práce s úložištěm Subversion](working-with-subversion.md)