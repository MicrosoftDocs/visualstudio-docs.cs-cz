---
title: Přihlášení ve Windows
description: Přečtěte si, jak se přihlásit k aplikaci Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b0ed679188cc0a4df9329fdd0adff4ad69667e6
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375757"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Přihlaste se do sady Visual Studio ve Windows.

I když se nemusíte přihlašovat, máte k dispozici mnoho výhod. Když se přihlásíte, můžete přizpůsobit, optimalizovat a rozšířit možnosti sady Visual Studio. 

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [přihlášení k Visual Studio pro Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> Pokud chcete pracovat s prostředky nakonfigurovanými pro podmíněný přístup, upgradujte na Visual Studio 2019 Update 16,6 nebo novější. Další informace najdete v tématu [Jak používat Visual Studio s účty, které vyžadují vícefaktorové ověřování](work-with-multi-factor-authentication.md).
> Použití sady Visual Studio 2017 pro přístup k prostředkům nakonfigurovaným pro podmíněný přístup může aktivovat omezené možnosti ověřování a vyzvat opakované ověření několikrát v rámci stejné relace sady Visual Studio. 
> 
::: moniker-end

## <a name="benefits"></a>Výhody

Tady je úplný seznam toho, co můžete očekávat a co můžete udělat po přihlášení:


#### <a name="extend-the-visual-studio-trial-period"></a>Prodloužení zkušebního období sady Visual Studio

Visual Studio Professional nebo Visual Studio Enterprise můžete použít po dobu dalších 90 dní, místo abyste byli omezeni na zkušební dobu 30 dní. Další informace najdete v tématu o [prodloužení zkušební verze nebo aktualizace licence](../ide/how-to-unlock-visual-studio.md).

#### <a name="synchronize-your-visual-studio-settings"></a>Synchronizace nastavení aplikace Visual Studio

Nastavení, které přizpůsobíte, například vazby kláves, rozložení okna a barevný motiv, se použijí okamžitě při přihlášení k aplikaci Visual Studio na libovolném zařízení. Viz [synchronizace nastavení v aplikaci Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

#### <a name="use-visual-studio-community-edition"></a>Použití Visual Studio Community Edition

Pokud vás instalace edice Community vyzve k zadání licence, přihlaste se k integrovanému vývojovému prostředí, abyste mohli dál používat Visual Studio Community **zdarma**. 

#### <a name="unlock-visual-studio-visual-studio-subscription-or-an-azure-devops-organization"></a>Odemknutí sady Visual Studio (předplatné sady Visual Studio nebo organizace Azure DevOps)

Pokud používáte účet, který je přidružený k předplatnému sady Visual Studio nebo organizaci Azure DevOps, použijte postup v části [prodloužení zkušební verze nebo aktualizace licence](../ide/how-to-unlock-visual-studio.md).

#### <a name="the-visual-studio-dev-essentials-program"></a>Visual Studio Dev Essentials program

Tento program zahrnuje bezplatné nabídky softwaru, školení, podporu a další. Další informace najdete v tématu [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) .

#### <a name="automatically-connect-to-services"></a>Automaticky se připojovat ke službám

Připojte se ke službám, jako je Azure a Azure DevOps Services, v prostředí IDE bez opětovného dotazování pro přihlašovací údaje pro stejný účet.

## <a name="how-to-sign-in"></a>Jak se přihlásit 

Při prvním otevření aplikace Visual Studio budete vyzváni k přihlášení a zadání některých základních registračních informací.

![Výzva k přihlášení](../ide/media/vs2019_signinpopup.png)

1. Vyberte účet Microsoft nebo pracovní nebo školní účet, který vás nejlépe zaznamená. Pokud nemáte žádné z těchto účtů, můžete účet Microsoft zdarma vytvořit kliknutím na odkaz pod tlačítkem přihlásit se. Pokud máte problémy, přečtěte si téma [návody registrace účet Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Vyberte nastavení uživatelského rozhraní a barevný motiv, který chcete použít v aplikaci Visual Studio. Visual Studio pamatuje tato nastavení a synchronizuje je ve všech prostředích sady Visual Studio, ke kterým jste se přihlásili. Seznam nastavení, která jsou synchronizovaná, najdete v tématu [synchronizovaná nastavení](../ide/synchronized-settings-in-visual-studio.md). Nastavení můžete později změnit, pokud otevřete   >  nabídku **Možnosti** nástrojů v aplikaci Visual Studio.
   Po zadání nastavení se spustí aplikace Visual Studio, přihlásíte se a budete připraveni začít. 
   
1. Chcete-li ověřit, zda jste přihlášeni, hledejte své jméno v pravém horním rohu prostředí sady Visual Studio.

![Aktuálně přihlášený uživatel v VS2019](../ide/media/vs2019_username.png)

Pokud se rozhodnete, že se nechcete přihlašovat při prvním spuštění sady Visual Studio, je snadné to provést později. Vyhledejte odkaz pro **přihlášení** v pravém horním rohu prostředí sady Visual Studio.

![Přihlášený uživatel](../ide/media/vs2019_usernotsignedin.png)

Pokud se odhlásíte, budete automaticky přihlášeni k aplikaci Visual Studio vždy, když ji spustíte, a všechny změny synchronizovaného nastavení se automaticky uplatní. Pokud se chcete odhlásit, klikněte na ikonu s názvem vašeho profilu v pravém horním rohu prostředí sady Visual Studio, vyberte příkaz **Nastavení účtu** a pak zvolte odkaz **Odhlásit** . Pokud se chcete znovu přihlásit, klikněte v pravém horním rohu prostředí sady Visual Studio na příkaz **Přihlásit** se.

## <a name="update-your-profile"></a>Aktualizace profilu

1. Přejít na   >  **Nastavení účtu** soubor a vyberte odkaz **Spravovat profil sady Visual Studio** .

1. V okně prohlížeče vyberte **Upravit profil** a změňte požadovaná nastavení.

1. Až skončíte, klikněte na **Uložit změny**.

## <a name="troubleshooting"></a>Řešení potíží

Nápovědu získáte na stránce [podpory předplatného](https://visualstudio.microsoft.com/subscriptions/support/) .

## <a name="see-also"></a>Viz také

* [Prodloužení zkušební verze nebo aktualizace licence](../ide/how-to-unlock-visual-studio.md)
* [Práce s účty GitHub v sadě Visual Studio](../ide/work-with-github-accounts.md)
* [Přehled integrovaného vývojového prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
