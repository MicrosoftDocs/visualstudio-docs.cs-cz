---
title: Prodloužení zkušební verze nebo aktualizace licence
description: Přečtěte si, jak rozšířit bezplatnou zkušební verzi sady Visual Studio, použít online předplatné nebo kód Product Key k odemknutí sady Visual Studio a aktualizovat zastaralou licenci nebo licenci s ukončenou platností.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8e11d77a94c7c1d3d7b038ecea1a6c61646e371f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027570"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Prodloužení zkušební verze nebo aktualizace licence

Můžete vyhodnotit bezplatnou zkušební verzi [Visual Studio Professional nebo Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) po dobu 30 dnů. A pokud se přihlásíte, můžete zkušební dobu prodloužit na 90 dní. (Visual Studio Community je zdarma bez zkušební doby. Musíte se [však pravidelně přihlašovat,](signing-in-to-visual-studio.md) abyste měli [licenci aktuální](#update-a-stale-license).)

Chcete-li aplikaci Visual Studio používat i po skončení zkušebního období, odemkněte ji [online předplatným](#use-an-online-subscription) nebo [kódem Product Key](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Použití online předplatného

1. Zvolte tlačítko **Přihlásit se** v pravém horním rohu ide (nebo přejděte na**Nastavení účtu** **souboru,** > chcete-li otevřít dialogové okno **Nastavení účtu,** a pak zvolte tlačítko **Přihlásit se).**

1. Zadejte přihlašovací údaje pro účet Microsoft nebo pracovní nebo školní účet. Visual Studio najde předplatné Visual Studia nebo organizaci Azure DevOps přidruženou k vašemu účtu.

> [!IMPORTANT]
> Visual Studio automaticky vyhledá přidružené online předplatná, když se připojíte k organizaci Azure DevOps z okna nástroje **Team Explorer.** Když se připojíte k organizaci Azure DevOps, můžete se přihlásit pomocí účtů Microsoft a práce nebo školy. Pokud pro tento uživatelský účet existuje online předplatné, Visual Studio automaticky odemkne rozhraní IDE za vás.

Další informace o předplatných Sady Visual Studio a jejich fungování najdete na stránce [Nejčastější dotazy k podpoře předplatných.](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="enter-a-product-key"></a>Zadání kódu Product Key

1. Vyberte**Nastavení účtu** **souboru,** >  **chcete-li** otevřít dialogové okno Nastavení účtu, a pak zvolte **odkaz Licence s kódem Product Key.**

1. Zadejte kód Product Key do poskytnutého prostoru.

> [!TIP]
> Předběžné verze sady Visual Studio nemají kódy Product Key. Chcete-li používat předběžné verze, musíte se přihlásit k ide.

Další informace o produktových klíčích sady Visual Studio pro Visual Studio a o tom, jak je získat, najdete na stránce [Použití kódů Product Key v předplatných sady Visual Studio.](/visualstudio/subscriptions/product-keys)

## <a name="update-a-stale-license"></a>Aktualizace zastaralé licence

V sadě Visual Studio se může zobrazit zpráva "Vaše licence zastaralá a musí být aktualizována."

![Zpráva o zastaralé licenci sady Visual Studio](../ide/media/vs2017_stale-license.png)

Tato zpráva označuje, že i když vaše předplatné může být stále platné, licenční token, který Visual Studio používá k udržení vašeho předplatného aktuální nebyl aktualizován. Visual Studio hlásí, že licence je zastaralá z jednoho z následujících důvodů:

* Nepoužili jste visual studio nebo jste se delší dobu nepřipojili k Internetu.
* Odhlásil jste se z Visual Studia.

Než licenční token zatuchne, Visual Studio nejprve zobrazí varovnou zprávu s žádostí o opětovné zadání přihlašovacích údajů.

Pokud pověření znovu nezadáte, token začne být zastaralý a v dialogovém okně **Nastavení účtu** se dozvíte, kolik dní vám zbývá, než platnost tokenu vyprší. Po vypršení platnosti tokenu je nutné znovu zadat přihlašovací údaje pro účet, abyste mohli pokračovat v používání sady Visual Studio.

> [!Important]
> Pokud používáte Visual Studio delší dobu v prostředích s omezeným nebo žádným přístupem k Internetu, měli byste použít kód Product Key k odemknutí sady Visual Studio, aby nedošlo k přerušení.

## <a name="update-an-expired-license"></a>Aktualizace licence, jejíž platnost vypršela

Pokud platnost vašeho předplatného vypršela a už nemáte přístupová práva k sadě Visual Studio, musíte předplatné obnovit nebo přidat jiný účet, který má předplatné. Další informace o licenci, kterou používáte, naleznete v**části Nastavení účtu** **souborů** > a informace o licenci na pravé straně dialogového okna. Pokud máte jiné předplatné přidružené k jinému účtu, přidejte tento účet do seznamu **Všechny účty** na levé straně dialogového okna výběrem odkazu **Přidat účet.**

## <a name="get-support"></a>Získat podporu

Někdy se věci pokazí. Pokud narazíte na problém, zde jsou některé možnosti podpory:

* Oznamte problémy s produktem pomocí nástroje [Nahlásit problém.](how-to-report-a-problem-with-visual-studio.md)
* Odpovědi na otázky týkající se předplatných, účtů a fakturace najdete v [nejčastějších dotazech k podpoře předplatných](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>Viz také

* [Přihlášení k sadě Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Porovnání edic Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [Další informace o předplatných Sady Visual Studio](/visualstudio/subscriptions/)
