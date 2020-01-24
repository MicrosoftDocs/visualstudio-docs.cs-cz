---
title: 'Postupy: spuštění nástroje Spy + + | Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542617"
---
# <a name="how-to-start-spy"></a>Postupy: Spuštění nástroje Spy++

Můžete spustit Spy + + buď ze sady Visual Studio, nebo na příkazovém řádku.

 Pokud spustíte příkaz Spy + +, zobrazí se zpráva s dotazem, zda chcete provést změny v počítači. Vyberte **Ano**.

> [!NOTE]
> Můžete spustit jenom jednu instanci nástroje Spy + +. Pokud se pokusíte spustit druhou instanci, stačí, když právě spuštěná instance získá fokus.

## <a name="prerequisites"></a>Požadavky

Spy + + vyžaduje následující součásti. Tyto komponenty můžete vybrat z Instalační program pro Visual Studio výběrem karty **jednotlivé součásti** a následným výběrem následujících součástí.

* V části ladění a testování vyberte  **C++ nástroje pro profilaci**
* V části vývojové aktivity vyberte  **C++ základní funkce.**

Pokud jste provedli nějaké změny, postupujte podle pokynů k instalaci těchto součástí.

## <a name="start-spy-from-visual-studio"></a>Spuštění nástroje Spy + + ze sady Visual Studio

V nabídce **nástroje** vyberte **Spy + +** .

Protože Spy + + běží nezávisle, po jeho spuštění můžete aplikaci Visual Studio zavřít.

> [!NOTE]
> Když protokoluje zprávy pomocí nástroje Spy + +, může to způsobit, že operační systém bude pracovat pomaleji.

## <a name="start-spy-at-a-command-prompt"></a>Spuštění nástroje Spy + + v příkazovém řádku

1. V okně příkazového řádku změňte adresáře do složky, která obsahuje Spyxx. exe. Cesta k této složce je obvykle..\\\\\Common7\Tools *instalační složky sady Visual Studio*.

2. Zadejte **Spyxx. exe**.

## <a name="see-also"></a>Viz také:
- [Použití nástroje Spy++](../debugger/using-spy-increment.md)
- [Zobrazení nástroje Spy++](../debugger/spy-increment-views.md)
- [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)
