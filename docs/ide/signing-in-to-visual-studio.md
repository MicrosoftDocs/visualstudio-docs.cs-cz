---
title: Přihlásit se
description: Přečtěte si, jak se přihlásit k Visual Studio.
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1335ab3d8f679f00fb7f52420d378baa1f2bd905
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222991"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>přihlášení k Visual Studio v Windows

I když se nemusíte přihlašovat, máte k dispozici mnoho výhod. když se přihlásíte, můžete přizpůsobit, optimalizovat a rozšířit možnosti Visual Studio. 

> [!NOTE]
> toto téma se týká Visual Studio Windows. Visual Studio pro Mac najdete v tématu [přihlášení k Visual Studio pro Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> pokud chcete pracovat s prostředky nakonfigurovanými pro podmíněný přístup, upgradujte na verzi Visual Studio 2019 Update 16,6 nebo novější. další informace najdete v tématu [použití Visual Studio s účty, které vyžadují službu multi-factor authentication](work-with-multi-factor-authentication.md).
> použití Visual Studio 2017 pro přístup k prostředkům nakonfigurovaným pro podmíněný přístup může aktivovat omezené možnosti ověřování a vyzvat opakované ověřování několikrát v rámci stejné relace Visual Studio. 
> 
::: moniker-end

## <a name="benefits"></a>Výhody

Tady je úplný seznam toho, co můžete očekávat a co můžete udělat po přihlášení:

|Výhoda|Description|
|---|---|
|prodloužení Visual Studio zkušebního období|použijte Visual Studio Professional nebo Visual Studio Enterprise **po dobu dalších 90 dní**, místo abyste byli omezeni na zkušební dobu 30 dní. <br/>Viz část [rozšiřování zkušební verze nebo aktualizace licence](../ide/how-to-unlock-visual-studio.md).|
|odemknout Visual Studio (Visual Studio předplatné nebo organizace Azure DevOps)|pokud používáte účet, který je přidružený k předplatnému Visual Studio nebo organizaci Azure DevOps, odemkněte Visual Studio.<br/>Viz část [rozšiřování zkušební verze nebo aktualizace licence](../ide/how-to-unlock-visual-studio.md).|
|synchronizace nastavení Visual Studio|Nastavení, které přizpůsobíte, například vazby klíčů, rozložení oken a barevný motiv, se okamžitě použijí při přihlášení k Visual Studio na jakémkoli zařízení. <br/>Viz [synchronizace nastavení v Visual Studio](../ide/synchronized-settings-in-visual-studio.md).|
|Automaticky se připojovat ke službám|Připojení ke službám, jako je Azure a Azure DevOps Services, v prostředí IDE bez nutnosti opětovného dotazování pro přihlašovací údaje pro stejný účet.|
|nadále používat edici Visual Studio Community|pokud vám instalace edice Community vyzve k zadání licence, přihlaste se k integrovanému vývojovému prostředí a pokračujte v používání Visual Studio Community **zdarma**. |
|Získat Visual Studio Dev Essentials|Tento program zahrnuje bezplatné nabídky softwaru, školení, podporu a další. <br/>viz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/).|


## <a name="how-to-sign-in"></a>Jak se přihlásit 

když poprvé otevřete Visual Studio, budete vyzváni k přihlášení a zadání některých základních registračních informací.

![Výzva k přihlášení](../ide/media/vs2019_signinpopup.png)

1. Vyberte účet Microsoft nebo pracovní nebo školní účet, který vás nejlépe zaznamená. Pokud nemáte žádné z těchto účtů, můžete účet Microsoft zdarma vytvořit kliknutím na odkaz pod tlačítkem přihlásit se. Pokud máte problémy, přečtěte si téma [návody registrace účet Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Vyberte nastavení uživatelského rozhraní a barevný motiv, který chcete použít v Visual Studio. Visual Studio pamatuje tato nastavení a synchronizuje je napříč všemi Visual Studio prostředími, ke kterým jste se přihlásili. Seznam nastavení, která jsou synchronizovaná, najdete v tématu [synchronizovaná nastavení](../ide/synchronized-settings-in-visual-studio.md). nastavení můžete později změnit, pokud   >  v Visual Studio otevřete nabídku **možnosti** nástrojů.
   Po zadání nastavení se spustí aplikace Visual Studio, přihlásíte se a budete připraveni začít. 
   
1. chcete-li ověřit, zda jste přihlášeni, hledejte své jméno v pravém horním rohu Visual Studio prostředí.

![Aktuálně přihlášený uživatel v VS2019](../ide/media/vs2019_username.png)

pokud se rozhodnete, že se nechcete přihlašovat při prvním otevření Visual Studio, je snadné to provést později. vyhledejte odkaz **přihlásit** se v pravém horním rohu Visual Studioho prostředí.

![Přihlášený uživatel](../ide/media/vs2019_usernotsignedin.png)

pokud se odhlásíte, budete automaticky přihlášeni k Visual Studio vždy, když ji spustíte, a všechny změny synchronizovaného nastavení se automaticky uplatní. pokud se chcete odhlásit, klikněte na ikonu s názvem vašeho profilu v pravém horním rohu Visual Studio prostředí, vyberte příkaz **nastavení účtu** a pak zvolte odkaz **odhlásit** se. pokud se chcete znovu přihlásit, klikněte na příkaz **přihlásit** v pravém horním rohu Visual Studio prostředí.

## <a name="update-your-profile"></a>Aktualizace profilu

1. přejít na   >  **účet souboru Nastavení** a vyberte odkaz **spravovat Visual Studio profil** .

1. V okně prohlížeče vyberte **Upravit profil** a změňte požadovaná nastavení.

1. Až skončíte, klikněte na **Uložit změny**.

## <a name="troubleshooting"></a>Řešení potíží

Nápovědu získáte na stránce [podpory předplatného](https://visualstudio.microsoft.com/subscriptions/support/) .
