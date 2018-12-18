---
title: Nástroje R pro Visual Studio – nejčastější dotazy
description: Nejčastější dotazy k R v sadě Visual Studio.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 29634d63cf8e898203ff4d72a23296bdb14019e0
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348486"
---
# <a name="frequently-asked-questions"></a>Nejčastější dotazy

## <a name="visual-studio-support"></a>Visual Studio – podpora

**Q. Funguje RTVS v OS X nebo Linux?**

A. RTVS je v současné době postavené na Visual Studio, která je jen pro Windows implementace. Společnost Microsoft pracuje podpory na Visual Studio Code a Visual Studio pro Mac. Odkazovat na [RTVS vydat #1295](https://github.com/Microsoft/RTVS/issues/1295).

**Q. Funguje RTVS edicích sady Visual Studio Express?**

A. Ne.

**Q. Můžete použít rozšíření sady Visual Studio s RTVS**

A. Absolutně. Ve skutečnosti tady je několik, které jsou pro osoby pracující s R.

- [VsVim pro vim klávesové zkratky](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor souborů markdown s živého náhledu](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Zobrazit [Visual Studio Marketplace](https://marketplace.visualstudio.com/) najít další.

**Q. Vzhledem k tomu, že v sadě Visual Studio je RTVS, to znamená, že R můžete snadno použít s C#, C++ a další jazyky Microsoft?**

A. Ne. RTVS je nástroj pro vývoj kód R a používá standardní nativní překladače r. Spolupráce mezi R a další jazyky se momentálně nepodporuje.

**Q. Funguje RTVS s neanglické národní prostředí?**

A. Verzi 1.0 RTVS je jenom pro angličtinu. Verze 1.1 bude lokalizovaný do stejné sady jazyky, které je samotnou sadu Visual Studio. Do té doby, použijte [language pack pro Visual Studio 2015 v angličtině](https://www.microsoft.com/download/details.aspx?id=48157), nebo v sadě Visual Studio 2017, spusťte instalační program a vyberte angličtiny na portálu **jazykových sad** kartu.

![Mezinárodní nastavení pro Visual Studio 2017](media/FAQ-international-settings.png)

**Q. Chci ve skutečnosti aktuální nastavení sady Visual Studio, ale chcete vyzkoušet nové nastavení pro datové vědy. Co mám dělat?**

A. Uložit aktuální nastavení sady Visual Studio pomocí **nástroje** > **nastavení importu a exportu**, přepněte se do nastavení datové vědy. Chcete-li obnovit uložená nastavení, použijte **nastavení importu a exportu** příkaz znovu.

**Q. Můžete ukládat Můj projekt sady Visual Studio do sdílené síťové složky?**

A. Ne, Visual Studio nepodporuje projekty načítání ze sdílené síťové složky.

## <a name="r-interpretersintegration"></a>Interpretů/integrace R

**Q. Jaké překladače jazyka r. RTVS funguje s?**

A. [CRAN r.](https://cran.r-project.org/), [Microsoft R Client a Microsoft Machine Learning Server](/machine-learning-server/)

**Q. Kde lze stáhnout tyto interpretů?**

A. Zobrazit [instalace](installing-r-tools-for-visual-studio.md).

Q **co je Microsoft R Server?**

A. R Server je původní název [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Q. Funguje s 32-bit Edition R RTVS?**

A. Ne, RTVS podporuje pouze 64bitové verze jazyka R spuštěná v 64bitové verzi Windows.

**Q. Funguje RTVS s Moje systému správy zdrojových kódů?**

A. Ano, můžete použít libovolný systém řízení zdroje, který je integrovaný do sady Visual Studio.

**Q. Co jsou doporučené *.gitignore* nastavení pro projekt RTVS?**

A. GitHub udržuje hlavní úložiště doporučené *.gitignore* soubory. Je možné ho tady uvidíte: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Vzdálené služby

Otázka: **Co je vzdálené služby v sadě Visual Studio?**

A. Vzdálené služby R pro Visual Studio můžete nastavit počítač pro Windows nebo Linuxem a potom k němu připojit z RTVS. Zobrazit [nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

Otázka: **Je RTVS připojit na Microsoft Machine Learning Server?**

A. Ne, protože Microsoft ML Server je jiné technologie a neposkytuje mechanismus stejné připojení jako vyžadují RTVS.

Otázka: **Je RTVS připojit k virtuálnímu počítači vytvořené pomocí image virtuálního počítače pro datové vědy v Azure?**

A. Ano. [virtuální počítač pro datové vědy – Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) předinstalovaného image se vzdálenou službou R pro Visual Studio.

Q, **RTVS můžete připojit ke vzdálenému počítači s nainstalovaným jazykem r.?**

Na vzdáleném počítači musí být některé služba naslouchá na požadavky spuštění kódu jazyka R, kód přijímání a odesílání výsledků zpět do klientského počítače. To je, co dělat vzdálenou službou R pro Visual Studio. Zobrazit [nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

Otázka: **Co je Vzdálená relace?**

A. Přečtěte si článek, [spustit na vzdáleném serveru](/machine-learning-server/r/how-to-execute-code-remotely) v dokumentaci k Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Vývoj RTVS a funkce

**Q. Funkce X nebyl nalezen, ale má RStudio ho!**

A. RStudio je fantastická a až po zralé prostředí IDE pro R, která byla vyvíjena po mnoho let. RTVS požádá o kritických funkcích, které potřebujete k dosažení úspěchu. Pomůže určit prioritu budoucí práci díky [RTVS průzkumu](https://www.surveymonkey.com/r/RTVS1) a soubor problémy na [Githubu](https://github.com/Microsoft/RTVS/issues/).

**Q. Můžu přispět k RTVS?**

A. Samozřejmě. Zdrojový kód se nachází [Githubu](https://github.com/microsoft/RTVS). Odeslání chyb a komentovat těch již zaznamenaná pomocí sledování problémů.

Můžete také můžete přispívat do této dokumentace&mdash;stačí vybrat **upravit** v pravém horním rohu jakékoli stránky příkaz. Komentáře k dokumentaci si také mohou, které můžete přidat v dolní části libovolné stránky.
