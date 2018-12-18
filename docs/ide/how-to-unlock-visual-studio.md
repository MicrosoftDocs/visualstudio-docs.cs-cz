---
title: 'Postupy: odemknout Visual Studio'
ms.date: 07/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0f77fb6bb22c82fb8f3bb0b3bf2a7a32a9be559
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542374"
---
# <a name="how-to-unlock-visual-studio"></a>Postupy: odemknout Visual Studio

Můžete si vyzkoušet Visual Studio zdarma až po dobu 30 dnů. Přihlašování do integrovaného vývojového prostředí rozšiřuje zkušební období na 90 dní. Chcete-li pokračovat pomocí sady Visual Studio, odemknete rozhraní IDE podle:

- prostřednictvím online předplatného

- zadání kódu product key

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Odemknout prostřednictvím online předplatného sady Visual Studio

K odemknutí sady Visual Studio pomocí předplatného sady Visual Studio nebo organizace Azure DevOps přidružené k účtu Microsoft nebo pracovní nebo školní účet:

1. Klikněte na **přihlášení** tlačítko v pravém horním rohu integrovaného vývojového prostředí (nebo můžete přejít na **souboru** > **nastavení účtu** otevřít **nastavení účtu**  dialogové okno a klikněte na kartu **přihlášení** tlačítko).

1. Zadejte přihlašovací údaje pro účet Microsoft nebo pracovní nebo školní účet. Visual Studio vyhledá předplatné sady Visual Studio nebo spojené s vaším účtem organizace Azure DevOps.

> [!IMPORTANT]
> Visual Studio online přidružených předplatných automaticky vyhledá, při připojení k organizaci Azure DevOps z **Team Exploreru** panelu nástrojů. Při připojení k organizaci Azure DevOps se můžete přihlásit pomocí Microsoft a pracovní nebo školní účty. Pokud pro tento uživatelský účet existuje s online předplatným, sada Visual Studio automaticky odemknout rozhraní IDE za vás.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>K odemknutí sady Visual Studio s kódem product key

1. Vyberte **souboru** > **nastavení účtu** otevřít **nastavení účtu** dialogové okno a klikněte na kartu **licence s kódem Product Key**odkaz.

Zadejte kód product key v poskytnutém prostoru.

> [!TIP]
> Předběžné verze sady Visual Studio nemají žádné kódy product key. Musíte se přihlásit k prostředí IDE použití předběžných verzí.

## <a name="address-license-problem-states"></a>Stavy problém licenční adresy

### <a name="update-stale-licenses"></a>Aktualizovat zastaralé licence

 Možná jste viděli následující zprávu, která vaše licence bude zastaralé v sadě Visual Studio, který čte, "vaše licence je prošlá a musí se aktualizovat."

 ![Zpráva zastaralé licence Visual Studio](../ide/media/vs2017_stale-license.png)

 Tato zpráva znamená, že vaše předplatné může být stále platná, licenci, kterou token Visual Studio používá k zajištění aktuálnosti vaše předplatné se aktualizují a je prošlá kvůli jednomu z následujících důvodů:

- Nepoužili sady Visual Studio nebo měli bez připojení k Internetu pro delší dobu.
- Odhlásili jste se od sady Visual Studio.

Předtím, než půjde zastaralé token licence, sada Visual Studio nejprve zobrazí zprávu upozornění s výzvou, abyste znovu zadat přihlašovací údaje.

Pokud není znovu zadat přihlašovací údaje, token se začne přejít zastaralé a **nastavení účtu** dialogové okno zjistíte, kolik dní zbývá před plně vyprší platnost tokenu. Po vypršení platnosti tokenu, je potřeba znovu zadat přihlašovací údaje pro tento účet nebo licenci s jinou metodu výše, než budete pokračovat, pomocí sady Visual Studio.

> [!Important]
> Pokud používáte Visual Studio po delší dobu v prostředích s omezením nebo bez připojení k Internetu, by měl použít kód product key k odemknutí sady Visual Studio, aby se předešlo výpadkům.

### <a name="update-expired-licenses"></a>Aktualizovat vypršela platnost licence

 Pokud vypršela platnost vašeho předplatného úplně a už nebude mít přístupová práva ke službě Visual Studio, musíte předplatné nebo přidat další účet, který má předplatné. Chcete-li zobrazit další informace o licenci, kterou používáte, přejděte na **souboru** > **nastavení účtu** a podívejte se na informace o licenci na pravé straně dialogového okna. Pokud máte jiné předplatné spojené s jiným účtem, přidejte daný účet do **všechny účty** seznamu na levé straně dialogového okna tak, že vyberete **přidat účet** odkaz.

## <a name="see-also"></a>Viz také:

* [Přihlášení k sadě Visual Studio](../ide/signing-in-to-visual-studio.md)