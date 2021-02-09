---
title: Instalace nástrojů R
description: Jak nainstalovat nástroje R v aplikaci Visual Studio 2017 a Visual Studio 2015, včetně offline instalací.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: fa5346d65a94646a0fa5e922f3b0055d8cdb6c0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908655"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Postup instalace Nástroje R pro Visual Studio

V tomto článku:

- [Podporované verze sady Visual Studio](#supported-versions-of-visual-studio)
- [Instalace RTVS v aplikaci Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Instalace RTVS v aplikaci Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Offline instalace](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Po instalaci nástrojů R budete možná chtít nakonfigurovat aplikaci Visual Studio pro optimalizované rozložení dat pro odborníky, jak je popsáno v článku [Možnosti](options-for-r-tools-in-visual-studio.md) .

## <a name="supported-versions-of-visual-studio"></a>Podporované verze sady Visual Studio

Nástroje R pro Visual Studio (RTVS) se podporuje ve Windows s edicemi Enterprise (Free), Professional a Enterprise sady [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a [Visual Studio 2015 Update 3 (nebo vyšší)](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) (přímým stažením).

RTVS není v Visual Studio pro Mac v současnosti podporován.

RTVS se neinstaluje, pokud máte pouze prostředí sady Visual Studio, které je součástí produktů, jako jsou Visual Studio Test Professional a SQL Server Management Studio. Prostředí sady Visual Studio neobsahuje potřebné komponenty pro RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Instalace RTVS v aplikaci Visual Studio 2017

1. Spusťte instalační program sady Visual Studio a vyberte možnost **Upravit** (podrobnosti najdete v tématu [Změna sady Visual Studio](../install/modify-visual-studio.md)). Pokud ještě nemáte nainstalovanou aplikaci Visual Studio, přečtěte si téma [instalace sady Visual Studio](../install/install-visual-studio.md). V systému Windows 7 se ujistěte, že je instalační program aktualizovaný, aby obsahoval aktualizaci Visual Studio 2017 verze *15,2 build 26430,12* nebo novější.

1. Vyberte úlohu pro **datové vědy a analytické aplikace** :

    ![Úlohy pro datové vědy a analytické aplikace v VS2017](media/installation-data-science-workload.png)

1. Nastavte další možnosti na pravé straně pod stejným názvem úlohy. Ve výchozím nastavení tato úloha zahrnuje podporu F # a Pythonu. Pro R je minimální požadavky **Podpora jazyka r**, **Podpora modulu runtime pro vývoj** v jazyce r a **Microsoft R Client**.

RTVS je nainstalován v: *% ProgramFiles (x86)% \ Microsoft Visual Studio \<version> \<edition> Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio* , kde *\<version>* je obvykle `2017` a *\<edition>* je `Community` , `Professional` nebo `Enterprise` .

## <a name="install-rtvs-in-visual-studio-2015"></a>Instalace RTVS v aplikaci Visual Studio 2015

V rámci sady Visual Studio 2015 je nutné nainstalovat Interpret R a nástroje jazyka r samostatně.

### <a name="install-an-r-interpreter"></a>Instalace překladače R

RTVS vyžaduje 64 verze R verze 3.2.1 nebo vyšší z jednoho nebo více následujících zdrojů:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open a CRAN R obě umožňují více souběžných verzí. Microsoft R Client však podporuje pouze jednu verzi a vždy používá nejnovější instalaci, kterou jste nainstalovali.

### <a name="install-the-r-tools"></a>Instalace nástrojů R

Stáhněte si aktuální RTVS pro Visual Studio 2015 z [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe) . RTVS vyhledá vhodnou verzi sady Visual Studio a pomůže vám nainstalovat překladač R, pokud jste to ještě neudělali.

> [!Note]
> Samostatný instalační program RTVS funguje pouze se sadou Visual Studio 2015; pomocí sady Visual Studio 2017 nainstalujte podporu R prostřednictvím [úlohy pro datové vědy a analytické aplikace](#install-rtvs-in-visual-studio-2017) popsané výše.

RTVS pro Visual Studio 2015 je nainstalovaný v: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Offline instalace sady Visual Studio a RTVS

Offline instalace je vhodná pro počítače, které nejsou připojené k Internetu:

1. Přejít na [vytvoření offline instalace sady Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Pokud používáte sadu Visual Studio 2015, v selektoru nad obsahem vyberte **2015** .

1. Postupujte podle pokynů pro vytvoření offline instalace na webové stránce.

1. Pro Visual Studio 2015 si stáhněte offline instalátory RTVS z [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) a [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip) .

1. Nainstalujte Visual Studio a RTVS z instalačních programů pro offline instalaci.

## <a name="see-also"></a>Viz také

- [Začínáme s R](getting-started-with-r.md)
- [Ukázkové projekty pro nástroje R](getting-started-samples.md)
- [Help v nástrojích jazyka R](getting-started-help.md)
- [Možnosti rozšíření Nástroje R](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (dřív R Server)](/machine-learning-server/)
