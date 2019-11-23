---
title: Nejčastější dotazy k Nástroje R pro Visual Studio
description: Nejčastější dotazy k R v aplikaci Visual Studio
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 4eef8e79023bdd3bde03fec33c16a1c8f6d90446
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306257"
---
# <a name="frequently-asked-questions"></a>Nejčastější dotazy

## <a name="visual-studio-support"></a>Podpora sady Visual Studio

**Otázka. RTVS funguje v OS X nebo Linux?**

A. RTVS je předem postavená na Visual Studio, což je implementace jenom pro Windows. Microsoft zkoumá podporu Visual Studio Code a Visual Studio pro Mac. Přečtěte si [RTVS #1295 problému](https://github.com/Microsoft/RTVS/issues/1295).

**Otázka. RTVS spolupracuje s edicemi Visual Studio Express?**

A. Ne.

**Otázka: můžu použít rozšíření sady Visual Studio s RTVS?**

A. Prosté. Tady je několik oblíbených pro lidi, kteří pracují s R.

- [VsVim pro vazby klíčů pro vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor Markdownu s živým náhledem](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Další informace najdete v [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

**Otázka. vzhledem k tomu, že RTVS je v aplikaci Visual Studio, znamená to, že R C#lze C++ snadno použít s a dalšími jazyky společnosti Microsoft?**

A. Ne. RTVS je nástroj pro vývoj kódu R a používá standardní nativní překladače R. Komunikace mezi R a dalšími jazyky není v současné době podporovaná.

**Otázka. RTVS pracuje s národním prostředím bez angličtiny?**

A. 1,0 verze RTVS je jenom v angličtině. Verze 1,1 bude lokalizována do stejné sady jazyků, jako je samotná sada Visual Studio. Mezitím použijte [anglickou jazykovou sadu pro Visual studio 2015](https://www.microsoft.com/download/details.aspx?id=48157)nebo v sadě visual Studio 2017, spusťte instalační program a vyberte angličtinu na kartě **jazykové sady** .

![Mezinárodní nastavení pro Visual Studio 2017](media/FAQ-international-settings.png)

**Otázka. mám v současnosti stejné nastavení sady Visual Studio, ale chci si vyzkoušet nové nastavení datové vědy. Co mám dělat?**

A. Pomocí **nástrojů** > **Nastavení importu a exportu**uložte aktuální nastavení sady Visual Studio a pak přepněte do nastavení datové vědy. Pro obnovení uložených nastavení použijte znovu příkaz **Import a export nastavení** .

**Otázka: mohu uložit projekt sady Visual Studio do sdílené síťové složky?**

A. Ne, Visual Studio nepodporuje načítání projektů ze sdílené síťové složky.

## <a name="r-interpretersintegration"></a>Překladače a integrace R

**Q. Jaké překladače R RTVS práci s?**

A. [Cran R](https://cran.r-project.org/), [Microsoft R Client a Microsoft Machine Learning Server](/machine-learning-server/)

**Otázka. kde mohu stáhnout tyto překladače?**

A. Viz [instalace](installing-r-tools-for-visual-studio.md).

**Co je Microsoft R Server?**

A. R Server je dřívější název [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Dotaz. RTVS pracuje s 32 edicemi jazyka R?**

A. Ne, RTVS podporuje jenom 64 edicí R, která běží na 64 edicích Windows.

**Dotaz RTVS spolupracuje se systémem správy zdrojového kódu?**

A. Ano, můžete použít libovolný systém správy zdrojového kódu, který je integrovaný do sady Visual Studio.

**Otázka. co je doporučené nastavení *gitignore* pro projekt RTVS?**

A. GitHub udržuje hlavní úložiště doporučených souborů *. gitignore* . Můžete ji zobrazit tady: [R. gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Vzdálené služby

Otázka: **Co jsou vzdálené služby v aplikaci Visual Studio?**

A. Vzdálená služba R Services pro Visual Studio umožňuje nastavit počítač s Windows nebo Linuxem a pak se k němu připojit z RTVS. Viz [Nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

Otázka: **Může se RTVS připojit k Microsoft Machine Learning Server?**

A. Ne, protože Microsoft ML Server je odlišná technologie a neposkytuje stejný mechanismus připojení, jaký vyžaduje RTVS.

Otázka: **Může se RTVS připojit k virtuálnímu počítači vytvořenému pomocí Data Science VM Image v Azure?**

A. Odpoví Image [Data Science VM-Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) je předinstalována se vzdálenými R Services pro Visual Studio.

Q, **může se RTVS připojit ke vzdálenému počítači s nainstalovaným jazykem R?**

Pokud chcete spustit kód R na vzdáleném počítači, musí se jednat o některé služby, které naslouchá požadavkům, přijímá kód a odesílá výsledky zpátky do klientského počítače. To je to, co dělají vzdálené služby R pro Visual Studio. Viz [Nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

Otázka: **Co je Vzdálená relace?**

A. Informace najdete v článku věnovaném [spuštění na vzdáleném serveru](/machine-learning-server/r/how-to-execute-code-remotely) v dokumentaci k Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Vývoj a funkce RTVS

**Otázka. funkce X chybí, ale RStudio má!**

A. RStudio je fantastická a vyspělé prostředí IDE pro R, které je ve vývoji po řadu let. RTVS vyhledává všechny důležité funkce, které je třeba provést úspěšně. Pomůžete určit prioritu budoucí práce při vytváření profilů problémů na [GitHubu](https://github.com/Microsoft/RTVS/issues/).

**Otázka: můžu přispívat do RTVS?**

A. Samozřejmě. Zdrojový kód bydlí na [GitHubu](https://github.com/microsoft/RTVS). Pomocí nástroje pro sledování problémů můžete odesílat chyby a komentovat ty, které už byly uloženy.

Také jste připraveni přispívat k této dokumentaci&mdash;stačí vybrat v pravém horním rohu libovolné stránky příkaz **Upravit** . Komentáře k dokumentům jsou také vítá vás, které můžete přidat v dolní části každé stránky.
