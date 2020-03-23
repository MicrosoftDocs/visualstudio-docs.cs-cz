---
title: Instalace nástrojů R
description: Jak nainstalovat nástroje R v sadě Visual Studio 2017 a Visual Studio 2015, včetně offline instalací.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: 5a09b3f78b929fd60764be36f56c0b580c7a42d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75843727"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Instalace nástrojů R pro sady Visual Studio

V tomto článku:

- [Podporované verze sady Visual Studio](#supported-versions-of-visual-studio)
- [Instalace RTVS v Sadě Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Instalace RTVS v Sadě Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Instalace offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Po instalaci nástroje R můžete nakonfigurovat visual studio pro optimalizované rozložení datových vědců, jak je popsáno v článku [Možnosti.](options-for-r-tools-in-visual-studio.md)

## <a name="supported-versions-of-visual-studio"></a>Podporované verze sady Visual Studio

Nástroje R pro Visual Studio (RTVS) jsou podporované v systému Windows s edicemi Community (free), Professional a Enterprise v jazyce [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i [Visual Studio 2015 Update 3 (nebo vyšší) (přímé](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) stahování).

RTVS není v současné době podporována na Visual Studio pro Mac.

RTVS se nenainstaluje, pokud máte jenom prostředí Visual Studio, které je součástí produktů, jako je Visual Studio Test Professional a SQL Server Management Studio. Visual Studio Shell postrádá potřebné součásti pro RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Instalace RTVS v Sadě Visual Studio 2017

1. Spusťte instalační program sady Visual Studio a vyberte možnost **Změnit** (podrobnosti viz [Úprava sady Visual Studio).](../install/modify-visual-studio.md) Pokud visual studio ještě nemáte nainstalovanou, [přečtěte si](../install/install-visual-studio.md)informace o instalaci Sady Visual Studio . Ve Windows 7 se ujistěte, že je instalační program aktualizován tak, aby zobrazoval visual studio 2017 verze *15.2 sestavení 26430.12* nebo novější.

1. Vyberte pracovní zátěž **pro datové vědy a analytické aplikace:**

    ![Pracovní zátěž pro datové vědy a analytické aplikace ve VS2017](media/installation-data-science-workload.png)

1. Nastavte všechny další možnosti na pravé straně pod stejným názvem pracovního vytížení. Ve výchozím nastavení tato úloha zahrnuje podporu F# a Pythonu. Pro R jsou minimální požadavky **podpora jazyka R**, podpora **runtime pro vývoj jazyka R**a klient microsoft **r**.

RtVS je nainstalován v `2017` aplikaci: *%ProgramFiles(x86)%\Microsoft Visual Studio\<verze>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio,* kde `Community` `Professional` `Enterprise` * \<* je verze>obvykle a * \<edice>* je , nebo .

## <a name="install-rtvs-in-visual-studio-2015"></a>Instalace RTVS v Sadě Visual Studio 2015

S Visual Studio 2015, budete muset nainstalovat překladač R a Nástroje R samostatně.

### <a name="install-an-r-interpreter"></a>Instalace překladače R

RTVS vyžaduje 64bitovou instalaci verze R 3.2.1 nebo vyšší z jednoho nebo více z následujících zdrojů:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Klient Microsoft R](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open a CRAN R umožňují více verzí vedle sebe. Microsoft R Client však podporuje pouze jednu verzi a vždy používá nejnovější verzi, kterou jste nainstalovali.

### <a name="install-the-r-tools"></a>Instalace nástrojů R

Stáhněte si aktuální RTVS pro Visual [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe)Studio 2015 z . RTVS zkontroluje vhodnou verzi sady Visual Studio a pomůže vám nainstalovat překladač R, pokud jste tak již neučinili.

> [!Note]
> Samostatný instalační program RTVS funguje pouze s Visual Studio 2015; s Visual Studio 2017 nainstalujte podporu R prostřednictvím [úlohy datové vědy a analytických aplikací,](#install-rtvs-in-visual-studio-2017) jak je popsáno výše.

RTVS pro Visual Studio 2015 je nainstalován v:`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Offline instalace sady Visual Studio a RTVS

Offline instalace je vhodná pro počítače, které nejsou připojeny k Internetu:

1. Přejděte na [Vytvoření offline instalace Sady Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Pokud používáte Visual Studio 2015, vyberte **2015** ve voliči nad obsahem.

1. Postupujte podle pokynů pro vytvoření offline instalace na webové stránce.

1. Pro Visual Studio 2015 stáhněte offline instalační [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip)programy RTVS z aplikace a .

1. Nainstalujte Visual Studio a RTVS z offline instalačních techniků.

## <a name="see-also"></a>Viz také

- [Začínáme s R](getting-started-with-r.md)
- [Ukázkové projekty nástrojů R](getting-started-samples.md)
- [Nápověda v nástrojích R](getting-started-help.md)
- [Možnosti nástrojů R](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (dříve R Server)](/machine-learning-server/)
