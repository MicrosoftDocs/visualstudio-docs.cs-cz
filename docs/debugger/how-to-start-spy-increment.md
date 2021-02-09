---
title: Spustit Spy + + | Microsoft Docs
description: Zjistěte, jak spustit nástroj Spy + + ze sady Visual Studio nebo na příkazovém řádku, pokud chcete ladit řešení.
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e8b1125534e52c810f97c91bd00ea53dfd3d6de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896626"
---
# <a name="how-to-start-spy"></a>Postupy: Spuštění nástroje Spy++

Můžete spustit Spy + + buď ze sady Visual Studio, nebo na příkazovém řádku.

 Pokud spustíte příkaz Spy + +, zobrazí se zpráva s dotazem, zda chcete provést změny v počítači. Vyberte **Ano**.

> [!NOTE]
> Můžete spustit jenom jednu instanci nástroje Spy + +. Pokud se pokusíte spustit druhou instanci, stačí, když právě spuštěná instance získá fokus.

## <a name="prerequisites"></a>Požadavky

Spy + + vyžaduje následující součásti. Tyto komponenty můžete vybrat z Instalační program pro Visual Studio výběrem karty **jednotlivé součásti** a následným výběrem následujících součástí.

* V části ladění a testování vyberte **Nástroje pro profilaci C++** .
* V části vývojářské aktivity vyberte **funkce C++ Core** .

Pokud jste provedli nějaké změny, postupujte podle pokynů k instalaci těchto součástí.

## <a name="start-spy-from-visual-studio"></a>Spuštění nástroje Spy + + ze sady Visual Studio

V nabídce **nástroje** vyberte **Spy + +**.

Protože Spy + + běží nezávisle, po jeho spuštění můžete aplikaci Visual Studio zavřít.

> [!NOTE]
> Když protokoluje zprávy pomocí nástroje Spy + +, může to způsobit, že operační systém bude pracovat pomaleji.

## <a name="start-spy-at-a-command-prompt"></a>Spuštění nástroje Spy + + v příkazovém řádku

1. V okně příkazového řádku změňte adresář na složku, která obsahuje spyxx.exe. Cesta k této složce je obvykle.. \\ *Instalační složka sady Visual Studio*\Common7\Tools \\ .

2. Zadejte **spyxx.exe**.

## <a name="see-also"></a>Viz také
- [Použití nástroje Spy++](../debugger/using-spy-increment.md)
- [Zobrazení nástroje Spy++](../debugger/spy-increment-views.md)
- [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)
