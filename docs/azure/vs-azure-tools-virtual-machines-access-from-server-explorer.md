---
title: Přístup k Azure Virtual Machines z Průzkumníka serveru | Dokumentace Microsoftu
description: Získat přehled o tom, jak zobrazit, vytvářet a spravovat virtuální počítače Azure (VM) v Průzkumníku serveru v sadě Visual Studio.
author: ghogen
manager: douge
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 1a353caf4781a2c321a8a0b385e023686ca78cde
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000101"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Přístup ke službě Azure Virtual Machines z Průzkumníka serveru

Pokud máte virtuální počítače hostované v Azure, můžete k nim přistupovat v Průzkumníku serveru. Musíte nejdřív se přihlásit ke svému předplatnému Azure pro zobrazení vašich mobilních službách. Pro přihlášení, otevřete místní nabídku pro uzel Azure v Průzkumníku serveru a zvolte **připojit se k Microsoft Azure**.

1. V Průzkumníku cloudu vyberte virtuální počítač a potom stisknutím klávesy F4 zobrazit její vlastnosti.

    Následující tabulka uvádí, které vlastnosti jsou k dispozici, ale jsou všechny jen pro čtení. Chcete-li změnit, použijte [webu Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040).

   | Vlastnost | Popis |
   | --- | --- |
   | Název DNS |Adresa URL s adresou Internetu z virtuálního počítače. |
   | Prostředí |Pro virtuální počítač hodnota této vlastnosti je vždy produkčního prostředí. |
   | Název |Název virtuálního počítače. |
   | Velikost |Velikost virtuálního počítače, která odráží objem paměti a místa na disku, který je k dispozici. Další informace najdete v tématu [velikostí virtuálních počítačů](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs). |
   | Stav |Mezi hodnoty patří spouštění, spuštěno, zastavení, zastaveno a stav načítání. Pokud se zobrazí stav načítání, aktuální stav neznámý. Hodnoty této vlastnosti se liší od hodnoty, které se používají na [webu Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). |
   | ID předplatného |ID předplatného pro váš účet Azure. Tyto informace můžete zobrazit na [webu Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040) zobrazením vlastností pro odběr. |
2. Zvolte některý uzel koncového bodu a následně zobrazit **vlastnosti** okna.
3. Následující tabulka popisuje dostupné vlastnosti koncových bodů, ale jsou jen pro čtení. Chcete-li přidat nebo upravit koncových bodů pro virtuální počítač, použijte [webu Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). 

   | Vlastnost | Popis |
   | --- | --- |
   | Název |Identifikátor pro koncový bod. |
   | Privátní Port |Port pro přístup k síti, interním do vaší aplikace. |
   | Protokol |Protokol, který používá přenosové vrstvy pro tento koncový bod TCP nebo UDP. |
   | Veřejný Port |Port, který se používá pro veřejný přístup k aplikaci. |
