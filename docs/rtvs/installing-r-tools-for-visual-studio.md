---
title: Instalace nástrojů R
description: Jak nainstalovat R Tools v sadě Visual Studio 2017 a Visual Studio 2015, včetně instalace v offline režimu.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 4fdf7cb791339350ff9644d0f727e3adc299add6
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220902"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Postup instalace nástroje R pro Visual Studio

V tomto článku:

- [Podporované verze sady Visual Studio](#supported-versions-of-visual-studio)
- [Nainstalujte RTVS v sadě Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Nainstalujte RTVS v sadě Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Offline instalace](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Po instalaci nástroje jazyka R, můžete chtít konfigurace sady Visual Studio rozložení mezi odborníky přes optimalizovaná data, jak je popsáno na [možnosti](options-for-r-tools-in-visual-studio.md) článku.

## <a name="supported-versions-of-visual-studio"></a>Podporované verze sady Visual Studio

Nástroje R pro Visual Studio (RTVS) se podporuje na Windows s Community (zdarma), Professional a verze Enterprise Edition obou [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) a [Visual Studio 2015 Update 3 (nebo vyšší)](http://go.microsoft.com/fwlink/?LinkId=691129) (s přímým přístupem ke stažení).

RTVS není podporována v současné době v sadě Visual Studio pro Mac.

RTVS nenainstaluje, pokud máte jenom prostředí sady Visual Studio, která je součástí produktů, jako je Visual Studio Test Professional a SQL Server Management Studio. Prostředí sady Visual Studio nemá potřebné součásti pro RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Nainstalujte RTVS v sadě Visual Studio 2017

1. Spusťte instalační program sady Visual Studio a vybrat **změnit** možnost (podrobnosti najdete v tématu [upravit Visual Studio](../install/modify-visual-studio.md)). Pokud ještě nemáte nainstalovanou sadu Visual Studio, přečtěte si téma [instalace sady Visual Studio](../install/install-visual-studio.md). Ve Windows 7, ujistěte se, že instalační program se aktualizuje a zobrazí Visual Studio 2017 verze *15.2 sestavení 26430.12* nebo novější.

1. Vyberte **pro datové vědy a analytické aplikace** úlohy:

    ![Pro datové vědy a analytické aplikace funkcí v VS2017](media/installation-data-science-workload.png)

1. Nastavte další možnosti na pravé straně pod stejným názvem úlohy. Ve výchozím nastavení, tato úloha zahrnuje F# a podpora jazyka Python. Pro jazyk R, jsou minimální požadavky **podpora jazyka R**, **podpora modulu CLR pro vývoj v jazyce R**, a **Microsoft R client**.

RTVS nainstalovaný v: *% ProgramFiles (x86) %\Microsoft Visual Studio\<verze >\<edition > Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio* kde  *\<verze >* je obvykle `2017` a  *\<edition >* je `Community`, `Professional`, nebo `Enterprise`.

## <a name="install-rtvs-in-visual-studio-2015"></a>Nainstalujte RTVS v sadě Visual Studio 2015

Pomocí sady Visual Studio 2015 musíte nainstalovat interpret R a nástroje jazyka R samostatně.

### <a name="install-an-r-interpreter"></a>Nainstalujte interpret R

RTVS vyžaduje 64bitové instalace jazyka R verze 3.2.1 nebo novější z jednoho nebo více z následujících zdrojů:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R.](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open a CRAN r. oba umožňují více verzí vedle sebe. Microsoft R Client, ale podporuje pouze jednu verzi a vždy používá nejnovější ten, který jste nainstalovali.

### <a name="install-the-r-tools"></a>Instalace nástrojů R

Stáhněte si aktuální RTVS pro Visual Studio 2015 z [ https://aka.ms/rtvs-current ](https://aka.ms/rtvs-current). RTVS kontroluje vhodnou verzi sady Visual Studio a vám pomůže s instalací interpretu r. Pokud jste tak již neučinili.

> [!Note]
> Samostatný instalační program RTVS funguje pouze s Visual Studio 2015; pomocí sady Visual Studio 2017, instalaci R podpory prostřednictvím [úloze datové vědy a analytické aplikace](#installing-rtvs-in-visual-studio-2017) jak je popsáno výše.

RTVS pro Visual Studio 2015 je nainstalován v: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Offline instalace sady Visual Studio a RTVS

Offline instalace je vhodný pro počítače, které nejsou připojené k Internetu:

1. Přejděte na [vytvoření offline instalace sady Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Pokud používáte Visual Studio 2015, vyberte **2015** v modulu pro výběr nad obsahu.

1. Postupujte podle pokynů pro vytvoření offline instalace na webové stránce.

1. Visual Studio 2015 a stáhnout RTVS instalační programy z [ https://aka.ms/rtvs-current-zip ](https://aka.ms/rtvs-current-zip) a [ https://aka.ms/rtvs-remote-zip ](https://aka.ms/rtvs-remote-zip).

1. Instalace sady Visual Studio a RTVS z offline instalační programy.

## <a name="see-also"></a>Viz také:

- [Začínáme s R](getting-started-with-r.md)
- [Nástroje R ukázkových projektů](getting-started-samples.md)
- [Nápověda v nástroje jazyka R](getting-started-help.md)
- [Možnosti nástrojů jazyka R](options-for-r-tools-in-visual-studio.md)
- [Server Microsoft Machine Learning (dříve R Server)](/machine-learning-server/)