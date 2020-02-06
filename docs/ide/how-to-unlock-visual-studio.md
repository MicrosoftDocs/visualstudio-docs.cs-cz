---
title: Prodloužení zkušební verze nebo aktualizace licence
description: Naučte se, jak můžete uvolnit bezplatnou zkušební verzi sady Visual Studio, používat online předplatné nebo kód Product Key k odemknutí sady Visual Studio a aktualizovat zastaralou nebo prošlou licenci.
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
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027570"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Prodloužení zkušební verze nebo aktualizace licence

Můžete vyhodnotit bezplatnou zkušební verzi [Visual Studio Professional nebo Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) po dobu 30 dnů. A pokud se přihlásíte, můžete zkušební období prodlouženi na 90 dní. (Visual Studio Community je zdarma bez zkušebního období. Musíte se ale pravidelně [přihlašovat](signing-in-to-visual-studio.md) , aby vaše licence zůstala v [aktuálním stavu](#update-a-stale-license).)

Pokud chcete Visual Studio po skončení zkušebního období dál používat, odemkněte ho pomocí [online předplatného](#use-an-online-subscription) nebo [kódu Product Key](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Použití online předplatného

1. Zvolte tlačítko **Přihlásit** v pravém horním rohu INTEGROVANÉho vývojového prostředí (nebo přejít na **soubor** > **Nastavení účtu** a otevřete dialog **Nastavení účtu** ) a pak zvolte tlačítko **Přihlásit** se.

1. Zadejte přihlašovací údaje pro účet Microsoft nebo pracovní nebo školní účet. Visual Studio najde předplatné sady Visual Studio nebo organizaci Azure DevOps, která je přidružená k vašemu účtu.

> [!IMPORTANT]
> Když se připojíte k organizaci Azure DevOps z okna nástroje **Team Explorer** , Visual Studio automaticky vyhledá přidružené online předplatné. Když se připojíte k organizaci Azure DevOps, můžete se přihlásit pomocí Microsoft i pracovního nebo školního účtu. Pokud pro tento uživatelský účet existuje s online předplatným, sada Visual Studio automaticky odemknout rozhraní IDE za vás.

Další informace o předplatných sady Visual Studio a o tom, jak fungují, najdete na stránce s [nejčastějšími dotazy pro předplatné support](https://visualstudio.microsoft.com/subscriptions/support/) .

## <a name="enter-a-product-key"></a>Zadejte kód Product Key.

1. Vyberte **soubor** > **Nastavení účtu** a otevřete dialogové okno **Nastavení účtu** a pak zvolte **licenci s odkazem na kód Product Key** .

1. Zadejte kód product key v poskytnutém prostoru.

> [!TIP]
> Předběžné verze sady Visual Studio nemají kódy Product Key. Chcete-li použít předběžné verze, je nutné se přihlásit k integrovanému vývojovému prostředí.

Další informace o klíčích produktu Visual Studio pro Visual Studio a o tom, jak je získat, najdete na stránce s informacemi o [používání kódů Product Key v předplatných sady Visual Studio](/visualstudio/subscriptions/product-keys) .

## <a name="update-a-stale-license"></a>Aktualizace zastaralé licence

V aplikaci Visual Studio se může zobrazit zpráva s informacemi o tom, že vaše licence prošla a je nutné ji aktualizovat. "

![Zpráva zastaralá licence sady Visual Studio](../ide/media/vs2017_stale-license.png)

Tato zpráva znamená, že i když vaše předplatné může být stále platné, neaktualizovalo se tím licenční token, který Visual Studio používá k zajištění aktuálnosti vašeho předplatného. Visual Studio hlásí, že licence je zastaralá z jednoho z následujících důvodů:

* Nepoužili jste aplikaci Visual Studio nebo jste po delší dobu nepřipojili k Internetu.
* Odhlásili jste se od sady Visual Studio.

Před zastaralým tokenem licence Visual Studio nejprve zobrazí zprávu s upozorněním, že je třeba znovu zadat přihlašovací údaje.

Pokud přihlašovací údaje nezadáte znovu, zahájí se platnost tokenu a dialogové okno **Nastavení účtu** vám ukáže, kolik dní zbývá ještě před vypršením platnosti tokenu. Po vypršení platnosti tokenu musíte znovu zadat svoje přihlašovací údaje pro účet, aby bylo možné pokračovat v používání sady Visual Studio.

> [!Important]
> Pokud používáte Visual Studio pro rozšířené tečky v prostředích s omezeným nebo žádným přístupem k Internetu, měli byste použít kód Product Key k odemknutí sady Visual Studio, abyste se vyhnuli přerušení.

## <a name="update-an-expired-license"></a>Aktualizace licence s vypršenou platností

Pokud vypršela platnost vašeho předplatného a už nemáte přístupová práva k aplikaci Visual Studio, musíte si obnovit předplatné nebo přidat další účet s předplatným. Pokud chcete zobrazit další informace o licenci, kterou používáte, přejděte na **soubor** > **Nastavení účtu** a podívejte se na informace o licencích na pravé straně dialogového okna. Pokud máte k jinému účtu přidruženo jiné předplatné, přidejte tento účet do seznamu **všechny účty** na levé straně dialogového okna tak, že vyberete odkaz **Přidat účet** .

## <a name="get-support"></a>Získat podporu

V některých případech se něco pokazilo. Pokud se setkáte s problémem, najdete tady některé možnosti podpory:

* Ohlaste problémy produktu pomocí nástroje [nahlásit problém](how-to-report-a-problem-with-visual-studio.md) .
* Odpovědi na dotazy týkající se předplatných, účtů a fakturace najdete v části [Nejčastější dotazy](https://visualstudio.microsoft.com/subscriptions/support/)k předplatným.

## <a name="see-also"></a>Viz také:

* [Přihlášení k sadě Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Porovnání edicí sady Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [Další informace o předplatných sady Visual Studio](/visualstudio/subscriptions/)
