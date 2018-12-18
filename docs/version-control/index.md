---
layout: LandingPage
title: Správa verzí
description: Průvodce Začínáme se správou verzí v sadě Visual Studio
keywords: VSTS, TFS, Správa verzí
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: 3640fba7d1ca3993841adb94dfdd08bc7d405e9b
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348159"
---
# <a name="version-control-in-visual-studio"></a>Správa verzí v sadě Visual Studio

Systémy správy verzí můžete sledovat změny kódu v čase. Při provádění změn, systém správy verzí pořídí snímek vašich souborů. Systém správy verzí ukládá snímky trvale, takže pokud ho potřebujete ji můžete odvolat později. Visual Studio poskytuje [Git](/azure/devops/repos/git/index?view=vsts) a [Team Foundation verze ovládacího prvku (TFVC)](/azure/devops/repos/tfvc/index?view=vsts). Při rozhodování mezi těmito dvěma systémy, najdete v článku [výběr správné správy verzí pro projekt](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git

Git je systém správy verzí nejčastěji používané ještě dnes a se rychle mění na standard pro správu verzí. Git je distribuovaný systém správy verzí, což znamená, že vaše místní kopie kódu je úložiště úplnou verzi ovládacího prvku. Zkontrolujte tyto plně funkční místní úložiště, které usnadňují vzdálenou nebo offline práci. Potvrďte svou práci místně a pak sesynchronizujete své úložiště s kopií na serveru. Toto paradigma se liší od centralizované správy verzí ve kterém klienti musí provést synchronizaci kódu serveru před vytvořením nové verze kódu.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Seznámení s Gitem</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Seznámení s Gitem v sadě Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Naklonování existujícího úložiště Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Team Foundation – správa verzí (TFVC) je centralizovaný systém správy verzí. Členové týmu mají zpravidla ve svých vývojových počítačích pouze jednu verzi každého souboru. Historická data se udržují pouze na serveru. Větve jsou založeny na cestě a vytvořeny na serveru.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Přečtěte si TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Začínáme s TFVC v sadě Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Kontrola kódu</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="resources"></a>Prostředky

- [Kniha pro Git](https://git-scm.com/book/en/v2)
- [Naplánujte si migraci na Git](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [Migrace od TFVC ke Gitu](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)
- [Správa verzí (Visual Studio for Mac)](/visualstudio/mac/version-control)