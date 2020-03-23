---
title: Nastavení úložiště Subversion
description: Použití Subversion v Visual Studiu pro Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 7d95c73b8d745826b256d515f161194ee9dbb587
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692388"
---
# <a name="set-up-a-subversion-repository"></a>Nastavení úložiště Subversion

Subversion je centralizovaný _systém správy verzí_, což znamená, že existuje jediný server, který obsahuje všechny soubory a revize, ze kterých mohou uživatelé rezervovat libovolnou verzi libovolného souboru. Když jsou soubory rezervovány ze vzdáleného úložiště Subversion, uživatel získá snímek úložiště v tomto okamžiku.

Chcete-li použít Subversion pro správu verzí, musí být nainstalována v počítači. Chcete-li zkontrolovat, zda je váš počítač nainstalován subversion, použijte v terminálu následující příkaz:

```bash
svn --version
```

Tento příkaz vrátí číslo verze.

Pokud Subversion ještě není nainstalován, nejjednodušší způsob, jak ji získat, je instalací _Nástrojů příkazového řádku Xcode_. Pomocí následujícího příkazu nainstalujte nástroje příkazového řádku Xcode a Subversion.

```bash
xcode-select --install
```

Jakmile je Subversion nainstalována na vašem počítači, použijte následující kroky k publikování projektu v SVN.

1. Vytvořte si online bezplatné úložiště SVN. V tomto příkladu byla [použita sestavení.](https://app.assembla.com/) Po vytvoření bude poskytnuta adresa URL, která bude použita pro připojení k úložišti:

    ![kopírování adresy URL SVN](media/version-control-subversion1-sml.png)

2. Otevřete nebo vytvořte Visual Studio pro Mac Project.

3. Klikněte pravým tlačítkem myši na projekt a vyberte možnost **Správa verzí > Publikovat v aplikaci Správa verzí...**:

    ![Zahájení publikování projektu](media/version-control-subversion2.png)

4. Na kartě **Připojit k úložišti** vyberte v horním rozevíracím souboru **Možnost Podverze.**

5. Zadejte adresu URL z kroku 1. Po zadání adresy URL jsou ve výchozím nastavení vyplněna ostatní pole:

    ![Dialogové okno Vybrat úložiště a zadat podrobnosti](media/version-control-subversion3.png)

7. Klepněte na tlačítko **OK** a potvrďte stisknutím **klávesy Publikovat**.

7. Pokud se zobrazí výzva, zadejte přihlašovací údaje pro web, na kterém úložiště vytvoříte, jak je znázorněno níže:

    ![Zadání přihlašovacích údajů pro repo podverze](media/version-control-subversion5.png)

8. Všechny příkazy správy verzí, které jsou k dispozici, by nyní měly být viditelné v nabídce správy verzí.

## <a name="see-also"></a>Viz také

- [Práce s úložištěm Subversion](working-with-subversion.md)