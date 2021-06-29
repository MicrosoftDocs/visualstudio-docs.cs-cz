---
title: Přístup k Azure Virtual Machines z Průzkumník serveru | Microsoft Docs
description: Získejte přehled o tom, jak zobrazit vytváření a správu virtuálních počítačů Azure v Průzkumník serveru v Visual Studio.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: ab67a81d761f2e17c82b75fb59a201188cf80986
ms.sourcegitcommit: b770b99034e65c91b29bea87bc6f5fa02348515b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2021
ms.locfileid: "112997628"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Přístup ke službě Azure Virtual Machines z Průzkumníka serveru

::: moniker range=">=vs-2022"
> [!Important]
> Uzel Azure pro Průzkumník serveru byl v roce 2022 Visual Studio vyřazen. Můžete použít Azure Portal nebo pokračovat v používání uzlu Azure v Průzkumník serveru předchozích verzích Visual Studio.
>
> Také [Průzkumník služby Microsoft Azure Storage](/azure/vs-azure-tools-storage-manage-with-storage-explorer) bezplatná samostatná aplikace od Microsoftu. Můžete ho použít k vizuální práci s daty Azure Storage Windows, macOS a Linuxu.
>
> Další informace o verzi Visual Studio 2022 najdete v naší zprávě [k vydání verze.](/visualstudio/releases/2022/release-notes-preview/)

::: moniker-end

::: moniker range="<=vs-2017"

Pokud máte virtuální počítače hostované v Azure, můžete k nim přistupovat v Průzkumník serveru. Abyste si mobilní služby prohlížet, musíte se nejdřív přihlásit ke svému předplatnému Azure. Pokud se chcete přihlásit, otevřete místní nabídku pro uzel Azure v Průzkumník serveru a zvolte Připojit k **Microsoft Azure**.

1. V Průzkumníku cloudu zvolte virtuální počítač a pak zvolte klávesu F4, aby se zobrazí okno jeho vlastností.

    Následující tabulka uvádí, které vlastnosti jsou k dispozici, ale všechny jsou jen pro čtení. Pokud je chcete změnit, použijte [Azure Portal](https://portal.azure.com).

   | Vlastnost | Popis |
   | --- | --- |
   | Název DNS |Adresa URL s internetovou adresou virtuálního počítače. |
   | Prostředí |U virtuálního počítače je hodnota této vlastnosti vždy Production (Produkční). |
   | Name |Název virtuálního počítače. |
   | Velikost |Velikost virtuálního počítače, která odráží velikost dostupné paměti a místa na disku. Další informace najdete v tématu [Velikosti virtuálních počítačů.](/azure/cloud-services/cloud-services-sizes-specs) |
   | Status |Mezi hodnoty patří Starting (Spuštění), Started (Spuštěno), Stopping (Zastavování), Stopped (Zastaveno) a Retrieving Status (Stav načítání). Pokud se zobrazí Stav načítání, aktuální stav je neznámý. Hodnoty této vlastnosti se liší od hodnot použitých v objektu [Azure Portal](https://portal.azure.com). |
   | ID předplatného |ID předplatného pro váš účet Azure. Tyto informace můžete zobrazit v [Azure Portal](https://portal.azure.com) zobrazením vlastností předplatného. |
2. Zvolte uzel koncového bodu a pak zobrazte **okno** Vlastnosti.
3. Následující tabulka popisuje dostupné vlastnosti koncových bodů, ale jsou jen pro čtení. Pokud chcete přidat nebo upravit koncové body pro virtuální počítač, použijte [Azure Portal](https://portal.azure.com).

   | Vlastnost | Popis |
   | --- | --- |
   | Název |Identifikátor koncového bodu. |
   | Privátní port |Port pro interní přístup k síti pro vaši aplikaci. |
   | Protokol |Protokol, který používá přenosová vrstva pro tento koncový bod, buď TCP, nebo UDP. |
   | Veřejný port |Port, který se používá pro veřejný přístup k vaší aplikaci. |

::: moniker-end