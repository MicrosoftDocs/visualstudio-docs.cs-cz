---
title: Odemčení sady Visual Studio 2015 | Microsoft Docs "
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a71a045661c48fd36733ecd8d2266470667a5c35
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670597"
---
# <a name="how-to-unlock-visual-studio"></a>Jak odemknout Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikaci Visual Studio můžete vyhodnotit zdarma až po dobu 30 dnů. Když se přihlásíte k prostředí IDE, můžete zkušební dobu rozšíříte o 90 dní. Chcete-li pokračovat v používání sady Visual Studio, můžete prostředí IDE odemknout pomocí

1. používání online předplatného.

2. zadání kódu Product Key.

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Odemčení sady Visual Studio pomocí online předplatného
 Chcete-li odemknout aplikaci Visual Studio pomocí předplatného MSDN nebo Visual Studio Online, které je přidruženo k účet Microsoft nebo pracovnímu nebo školnímu účtu:

1. Klikněte na tlačítko přihlásit v pravém horním rohu integrovaného vývojového prostředí (nebo přejděte na soubor > Nastavení účtu, otevřete dialogové okno nastavení účtu a klikněte na tlačítko Přihlásit se).

2. Zadejte přihlašovací údaje pro účet Microsoft nebo pracovní nebo školní účet. Visual Studio najde předplatné MSDN nebo Visual Studio Team Services předplatné spojené s vaším účtem.

> [!IMPORTANT]
> Když se připojíte k účtu Visual Studio Team Services z okna nástroje Team Explorer, Visual Studio automaticky vyhledá přidružené online předplatné. Když se připojíte k účtu Visual Studio Team Services, můžete se přihlásit pomocí Microsoft i pracovních nebo školních účtů. Pokud pro tento uživatelský účet existuje online předplatné, Visual Studio automaticky odemkne integrované vývojové prostředí (IDE).

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Odemčení sady Visual Studio s použitím kódu Product Key

1. Vyberte **soubor > nastavení účtu** a otevřete dialogové okno nastavení účtu a klikněte na odkaz**licence s použitím kódu Product Key**.

2. Zadejte kód Product Key v zadaném prostoru.

> [!TIP]
> Předprodejní verze sady Visual Studio nemají kódy Product Key. Abyste mohli používat předběžné verze, musíte se přihlásit k integrovanému vývojovému prostředí.

## <a name="addressing-license-problem-states"></a>Stavy řešení potíží s licencemi

### <a name="updating-stale-licenses"></a>Aktualizace zastaralých licencí
 Možná jste viděli následující zprávu, že vaše licence v nástroji Visual Studio prochází.

 ![Dialogové okno informace o uživateli sady Visual Studio](../ide/media/vs2013-userinfo.png "VS2013_UserInfo")

 Tato zpráva znamená, že i když může být předplatné stále platné, aplikace Visual Studio s tokenem licence zachová aktuální předplatné a v důsledku toho je zastaralá kvůli jednomu z následujících důvodů:

1. Nepoužívali jste aplikaci Visual Studio nebo nemáte k dispozici žádné připojení k Internetu po delší dobu.

2. Odhlásili jste se od sady Visual Studio.

   Před ukončením licenčního tokenu se v aplikaci Visual Studio nejprve zobrazí varovná zpráva s výzvou k opětovnému zadání přihlašovacích údajů.

   Pokud nezadáte svoje přihlašovací údaje znovu, začne se token zastaralý. Pokud k tomu dojde, zobrazí se v dialogovém okně nastavení účtu, kolik dní zbývá před vypršením platnosti tokenu. Po vypršení platnosti tokenu budete muset znovu zadat svoje přihlašovací údaje pro tento účet nebo licenci s jinou metodou výše, než budete moct pokračovat v používání sady Visual Studio.

> [!IMPORTANT]
> Pokud používáte Visual Studio pro rozšířené tečky v prostředích s omezeným nebo žádným přístupem k Internetu, měli byste použít kód Product Key k odemknutí sady Visual Studio, abyste se vyhnuli přerušení.

### <a name="updating-expired-licenses"></a>Aktualizace licencí s vypršenou platností
 Pokud vašemu předplatnému vypršela platnost a už nemáte přístupová práva k aplikaci Visual Studio, musíte:

1. Obnovte si předplatné. Pokud chcete zobrazit další informace o licenci, kterou používáte, přejděte na dialogové okno nastavení účtu > a podívejte se na informace o licencích na pravé straně dialogového okna.

2. Pokud máte jiné předplatné přidružené k jinému účtu, přidejte tento účet do seznamu všechny účty na levé straně dialogového okna nastavení účtu >, a to tak, že kliknete na Přidat účet... propojit.

## <a name="see-also"></a>Viz také
 [Přihlášení k sadě Visual Studio](../ide/signing-in-to-visual-studio.md)
