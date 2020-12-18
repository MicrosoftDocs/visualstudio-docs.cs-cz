---
title: Přihlášení k sadě Visual Studio
description: Přečtěte si, jak se přihlásit k aplikaci Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87c0ad7517bb01aa68d98e0502e34af7c767e962
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683993"
---
# <a name="sign-in-to-visual-studio"></a>Přihlášení k sadě Visual Studio

Můžete přizpůsobit a optimalizovat vývojové prostředí v aplikaci Visual Studio přihlášením k vašemu účtu přizpůsobení.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [přihlášení k Visual Studio pro Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [! Upozornění] použití sady Visual Studio 2017 pro přístup k prostředkům, které jsou nakonfigurovány pro podmíněný přístup, může aktivovat omezené možnosti ověřování a vyzvat opakované ověřování několikrát v rámci stejné relace sady Visual Studio. 
> Pokud chcete pracovat s prostředky nakonfigurovanými pro podmíněný přístup, upgradujte na Visual Studio 2019 Update 16,6 nebo novější. Další informace najdete v tématu [Jak používat Visual Studio s účty, které vyžadují vícefaktorové ověřování](work-with-multi-factor-authentication.md).

::: moniker-end

## <a name="why-should-i-sign-in-to-visual-studio"></a>Proč se bych se měl(a) přihlásit do aplikace Visual Studio?

Když se přihlašujete, vylepšit prostředí sady Visual Studio. Když se například přihlásíte, můžete [synchronizovat nastavení](synchronized-settings-in-visual-studio.md) napříč zařízeními, rozšíříte zkušební verzi a automaticky se připojíte ke službě Azure, abyste pojmenovat několik.

Tady je úplný seznam toho, co můžete očekávat a co můžete udělat po přihlášení:
- **Prodloužení zkušebního období sady Visual Studio** – můžete použít Visual Studio Professional nebo Visual Studio Enterprise po dobu dalších 90 dní, a nikoli omezit na zkušební dobu 30 dní. Další informace najdete v tématu o [prodloužení zkušební verze nebo aktualizace licence](../ide/how-to-unlock-visual-studio.md).

- **Pokračujte v používání sady Visual Studio Community Edition** – Pokud vás instalace edice Community vyzve k zadání licence, přihlaste se k integrovanému vývojovému prostředí a pokračujte v používání sady Visual Studio Community **zdarma**. 

- **Pokud používáte účet, který je přidružený k předplatnému sady Visual Studio nebo organizaci Azure DevOps, odemkněte Visual Studio**. Podrobné pokyny najdete v tématu [prodloužení zkušební verze nebo aktualizace licence](../ide/how-to-unlock-visual-studio.md).

- **Přístup k Visual Studio Dev Essentials programu** – tento program zahrnuje bezplatné nabídky softwaru, školení, podporu a další. Další informace najdete v tématu [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) .

- **Synchronizovat nastavení aplikace Visual Studio** – nastavení, které přizpůsobíte, například vazby klíčů, rozložení oken a barevný motiv, se použijí okamžitě při přihlášení k aplikaci Visual Studio na libovolném zařízení. Viz [synchronizace nastavení v aplikaci Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

- **Automatické připojení ke službám, jako je Azure a Azure DevOps Services** v prostředí IDE, bez nutnosti opětovného zobrazení výzvy k zadání přihlašovacích údajů pro stejný účet.

## <a name="how-to-sign-in-to-visual-studio"></a>Jak se přihlásit k Visual Studiu

Při prvním otevření aplikace Visual Studio budete vyzváni k přihlášení a zadání některých základních registračních informací.

![Výzva k přihlášení](../ide/media/vs2019_signinpopup.png)

Měli byste zvolit účet Microsoft nebo pracovní nebo školní účet, který vás nejlépe zaznamená. Pokud nemáte žádné z těchto účtů, můžete účet Microsoft zdarma vytvořit kliknutím na odkaz pod tlačítkem přihlásit se. Pokud máte problémy, přečtěte si téma [návody registrace účet Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

Dále zvolte nastavení uživatelského rozhraní a barevný motiv, který chcete použít v aplikaci Visual Studio. Visual Studio pamatuje tato nastavení a synchronizuje je ve všech prostředích sady Visual Studio, ke kterým jste se přihlásili. Seznam nastavení, která jsou synchronizovaná, najdete v tématu [synchronizovaná nastavení](../ide/synchronized-settings-in-visual-studio.md). Nastavení můžete později změnit, pokud otevřete   >  nabídku **Možnosti** nástrojů v aplikaci Visual Studio.

Po zadání nastavení se spustí aplikace Visual Studio, přihlásíte se a budete připraveni začít. Chcete-li ověřit, zda jste přihlášeni, hledejte své jméno v pravém horním rohu prostředí sady Visual Studio.

![Aktuálně přihlášený uživatel v VS2019](../ide/media/vs2019_username.png)

Pokud se rozhodnete, že se nechcete přihlašovat při prvním spuštění sady Visual Studio, je snadné to provést později. Vyhledejte odkaz pro **přihlášení** v pravém horním rohu prostředí sady Visual Studio.

![Přihlášený uživatel](../ide/media/vs2019_usernotsignedin.png)

Pokud se odhlásíte, budete automaticky přihlášeni k aplikaci Visual Studio vždy, když ji spustíte, a všechny změny synchronizovaného nastavení se automaticky uplatní. Pokud se chcete odhlásit, klikněte na ikonu s názvem vašeho profilu v pravém horním rohu prostředí sady Visual Studio, vyberte příkaz **Nastavení účtu** a pak zvolte odkaz **Odhlásit** . Pokud se chcete znovu přihlásit, klikněte v pravém horním rohu prostředí sady Visual Studio na příkaz **Přihlásit** se.

## <a name="to-change-your-profile-information"></a>Změna informací v profilu

1. Přejít na   >  **Nastavení účtu** soubor a vyberte odkaz **Spravovat profil sady Visual Studio** .

1. V okně prohlížeče vyberte **Upravit profil** a změňte požadovaná nastavení.

1. Až skončíte, klikněte na **Uložit změny**.

## <a name="troubleshooting"></a>Řešení potíží

Pokud narazíte na problémy při přihlašování, získáte pomoc na stránce [podpory předplatného](https://visualstudio.microsoft.com/subscriptions/support/) .

## <a name="see-also"></a>Viz také

* [Prodloužení zkušební verze nebo aktualizace licence](../ide/how-to-unlock-visual-studio.md)
* [Práce s účty GitHub v sadě Visual Studio](../ide/work-with-github-accounts.md)
* [Přehled integrovaného vývojového prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
* [Přihlásit se (Visual Studio pro Mac)](/visualstudio/mac/signing-in)
* [Aktivace (Visual Studio pro Mac)](/visualstudio/mac/activation)
