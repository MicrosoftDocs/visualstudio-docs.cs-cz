---
title: Přístup k Azure Virtual Machines z Průzkumník serveru | Microsoft Docs
description: Získejte přehled o tom, jak zobrazit vytváření a správu virtuálních počítačů Azure v Průzkumník serveru v systému Visual Studio.
author: ghogen
manager: jillfra
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 8fd5d81e721bc2df7041d4cb724687e5ee540a7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911661"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Přístup ke službě Azure Virtual Machines z Průzkumníka serveru

Pokud máte virtuální počítače hostované v Azure, můžete k nim přistupovat v Průzkumník serveru. Abyste mohli zobrazit vaše mobilní služby, musíte se nejdřív přihlásit k předplatnému Azure. Pokud se chcete přihlásit, otevřete místní nabídku uzlu Azure v Průzkumník serveru a vyberte **připojit k Microsoft Azure**.

1. V Průzkumníku cloudu zvolte virtuální počítač a potom stisknutím klávesy F4 zobrazte okno vlastností.

    V následující tabulce jsou uvedeny vlastnosti, které jsou k dispozici, ale všechny jsou jen pro čtení. Pokud je chcete změnit, použijte [Azure Portal](https://portal.azure.com).

   | Vlastnost | Popis |
   | --- | --- |
   | Název DNS |Adresa URL s internetovou adresou virtuálního počítače |
   | Prostředí |U virtuálního počítače je hodnota této vlastnosti vždy produkční. |
   | Název |Název virtuálního počítače |
   | Velikost |Velikost virtuálního počítače, která odráží množství paměti a místa na disku, které je k dispozici. Další informace najdete v tématu [velikosti virtuálních počítačů](/azure/cloud-services/cloud-services-sizes-specs). |
   | Status |Mezi hodnoty patří spuštění, spuštění, zastavení, zastavení a načítání stavu. Pokud se zobrazí stav načítání, aktuální stav je neznámý. Hodnoty této vlastnosti se liší od hodnot používaných v [Azure Portal](https://portal.azure.com). |
   | SubscriptionID |ID předplatného pro váš účet Azure. Tyto informace o [Azure Portal](https://portal.azure.com) můžete zobrazit zobrazením vlastností předplatného. |
2. Zvolte uzel koncového bodu a pak zobrazte okno **vlastnosti** .
3. Následující tabulka popisuje dostupné vlastnosti koncových bodů, ale jsou jen pro čtení. K přidání nebo úpravě koncových bodů pro virtuální počítač použijte [Azure Portal](https://portal.azure.com).

   | Vlastnost | Popis |
   | --- | --- |
   | Název |Identifikátor koncového bodu. |
   | Privátní port |Port pro interní přístup k síti vaší aplikace |
   | Protokol |Protokol, který používá transportní vrstva pro tento koncový bod, buď TCP, nebo UDP. |
   | Veřejný port |Port, který se používá pro veřejný přístup k vaší aplikaci. |
