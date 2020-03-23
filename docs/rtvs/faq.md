---
title: R Nástroje pro Visual Studio nejčastější dotazy
description: Často kladené otázky na R v sadě Visual Studio.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 4eef8e79023bdd3bde03fec33c16a1c8f6d90446
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72306257"
---
# <a name="frequently-asked-questions"></a>Nejčastější dotazy

## <a name="visual-studio-support"></a>Podpora pro Visual Studio

**Otázka: Funguje RTVS na OS X nebo Linuxu?**

A. RTVS je v současné době postavena na visual studio, což je implementace jejeno systémwindows. Společnost Microsoft zkoumá podporu v aplikacích Visual Studio Code a Visual Studio for Mac. Informace o [problému RTVS naleznete #1295](https://github.com/Microsoft/RTVS/issues/1295).

**Otázka: Funguje RTVS s edicemi Visual Studio Express?**

A. Ne.

**Otázka: Můžu používat rozšíření sady Visual Studio s RTVS?**

A. Jistě. Ve skutečnosti, zde je několik, které jsou populární pro lidi pracující s R.

- [VsVim pro vazby klíčů Vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHubu](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor Markdown s živým náhledem](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Další informace najdete na [webu Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

**Dotaz: Vzhledem k tomu, že RTVS je v sadě Visual Studio, znamená to, že R lze snadno použít s C#, C++ a dalšími jazyky Microsoftu?**

A. Ne. RTVS je nástroj pro vývoj R kódu a používá standardní nativní R interprety. Interop mezi R a jinými jazyky není v současné době podporován.

**Otázka: Funguje RTVS s neanglickým národním prostředím?**

A. Verze RTVS 1.0 je pouze v angličtině. Verze 1.1 bude lokalizována do stejné sady jazyků, které visual studio sám je. Mezitím použijte [anglickou jazykovou sadu pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157)nebo Visual Studio 2017, spusťte instalační program a na kartě **Jazykové sady** vyberte angličtinu.

![Mezinárodní nastavení pro Visual Studio 2017](media/FAQ-international-settings.png)

**Otázka: Opravdu se mi líbí moje aktuální nastavení sady Visual Studio, ale chci vyzkoušet nové nastavení datové vědy. Co mám dělat?**

A. Uložte aktuální nastavení sady Visual Studio pomocí**nastavení importu a exportu** **nástrojů** > a přepněte na nastavení datové vědy. Chcete-li obnovit uložená nastavení, použijte znovu příkaz **Nastavení importu a exportu.**

**Otázka: Lze uložit projekt sady Visual Studio do sdílené síťové složky?**

A. Ne, Visual Studio nepodporuje načítání projektů ze sdílené síťové složky.

## <a name="r-interpretersintegration"></a>R tlumočníci/integrace

**Otázka: S jakými tlumočníky R rtvs pracuje?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client a Microsoft Machine Learning Server](/machine-learning-server/)

**Otázka: Kde mohu stáhnout tyto tlumočníky?**

A. Viz [Instalace](installing-r-tools-for-visual-studio.md).

Q **Co je Microsoft R Server?**

A. R Server je dřívější název [serveru Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Otázka: Funguje RTVS s 32bitovými edicemi R?**

A. Ne, RTVS podporuje pouze 64bitové edice R spuštěné v 64bitových edicích systému Windows.

**Otázka: Funguje RTVS s mým systémem správy zdrojového kódu?**

A. Ano, můžete použít libovolný systém správy zdrojového kódu, který je integrován do sady Visual Studio.

**Otázka: Jaká jsou doporučená nastavení *.gitignore* pro projekt RTVS?**

A. GitHub udržuje hlavní úložiště doporučených souborů *.gitignore.* Můžete vidět zde: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Vzdálené služby

Otázka: **Co je vzdálené služby v sadě Visual Studio?**

A. Služba Remote R Services for Visual Studio umožňuje nastavit počítač se systémem Windows nebo Linux a připojit se k němu z rtvs. Viz [Nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

Otázka: **Může se RTVS připojit k serveru Microsoft Machine Learning Server?**

A. Ne, protože Microsoft ML Server je jiná technologie a neposkytuje stejný mechanismus připojení, jak to vyžaduje RTVS.

Otázka: **Může se RTVS připojit k virtuálnímu počítači vytvořenému pomocí image virtuálního počítače pro datové vědy v Azure?**

A. Ano, je to tak. Image [virtuálního zařízení pro datové vědy – bitová kopie systému Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) je předinstalována se službou Remote R Services for Visual Studio.

Q, **MŮŽE RTVS připojit ke vzdálenému počítači s nainstalovaným R?**

Chcete-li spustit kód R na vzdáleném počítači, musí existovat nějaká služba, která naslouchá požadavkům, přijímá kód a odesílá výsledky zpět do klientského počítače. To je to, co vzdálené služby R pro visual studio. Viz [Nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

Otázka: **Co je vzdálená relace?**

A. Podívejte se na článek [Spustit na vzdáleném serveru](/machine-learning-server/r/how-to-execute-code-remotely) v dokumentaci k serveru Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Vývoj rtvs a funkce

**Otázka: Funkce X chybí, ale RStudio ji má!**

A. RStudio je fantastické a zralé IDE pro R, které je ve vývoji již mnoho let. RTVS se snaží mít všechny důležité funkce, které potřebujete k úspěchu. Pomozte upřednostnit budoucí práci podáním problémů na [GitHubu](https://github.com/Microsoft/RTVS/issues/).

**Otázka: Mohu přispět do RTVS?**

A. Samozřejmě. Zdrojový kód žije na [Githubu](https://github.com/microsoft/RTVS). Pomocí nástroje pro sledování problémů můžete odeslat chyby a komentovat již podané chyby.

Můžete také přispět do této&mdash;dokumentace a stačí vybrat příkaz **Upravit** v pravém horním pravém horním části libovolné stránky. Komentáře k dokumentům jsou také vítány, které můžete přidat v dolní části libovolné stránky.
