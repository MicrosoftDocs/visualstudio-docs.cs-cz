---
title: Shromažďovat data vzorkování Line-Level | Microsoft Docs
description: Přečtěte si, jak může vzorkování na úrovni řádků profileru odhalit kód, který používá velké množství času procesoru. Funguje s spravovaným i nativním kódem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3a760980b16fab17fed7180b0bc74e0271c61e1d
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801062"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Postupy: shromažďování dat vzorkování na úrovni řádků
Vzorkování na úrovni řádků je schopnost profileru určit, kde v kódu funkce náročné na procesor, jako je například funkce, která má vysoce exkluzivní ukázky, musí procesor strávit nejvíc času.

## <a name="overview"></a>Přehled
 Pro vzorkování na úrovni řádků Profiler provede v nastavených intervalech zásobník volání programu a agreguje tyto výsledky. Tyto výsledky zobrazují informace o tom, jaké pokyny byl procesor spuštěn při pořízení vzorků. Shromážděná data o exkluzivních ukázkách se pak analyzují, aby identifikovala řádky kódu a ukazatel na instrukce (IP).

 Vzorkování na úrovni řádků funguje pro spravovaný i nativní kód. Sestavy výkonu, které zobrazují tato data, zahrnují zobrazení řádků a zobrazení modulů.

 Pro nativní kód nejsou k dispozici informace o počátečním/koncovém znaku. Pro víceřádkové příkazy nejsou k dispozici informace o zahájení řádku pro nativní kód; k dispozici jsou pouze informace o koncích řádků.

### <a name="available-data"></a>Dostupná data
 Dostupná data vzorkování na úrovni řádků obsahují následující informace:

- Název funkce

- Adresa funkce

- Řádky začínající číslem řádku s ukázkovým kódem.

- Koncový řádek koncového čísla řádku To je obvykle stejné jako při "řádku begin" data kromě případů, kdy jeden program zahrnuje více řádků zdrojového kódu.

- Znaky začátku – počáteční sloupec agregované ukázky. Obvykle se jedná o 0 s výjimkou případů, kdy jeden řádek obsahuje více příkazů programu.

- Koncový sloupec znaků – konečný vzorek agregace

- IP adresa, na které se provedla agregovaná ukázka (jenom zobrazení IP).

  V zobrazení **modulů** , pokud funkce obsahuje statistiku na úrovni řádků, statistika je vnořena do každé funkce. Kromě toho se zobrazí statistiky na úrovni protokolu IP, které jsou vnořené pod každým řádkem.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Vypnout vzorkování na úrovni řádků pro spravovaný kód
 Ve výchozím nastavení je vzorkování na úrovni řádků zapnuté. Shromažďování dat na úrovni řádků pro spravovaný kód můžete vypnout pomocí jednoho z následujících příkazů:

- Před profilací zadejte **VSPerfCLREnv/samplelineoff**. To má vliv na aplikace i služby.

     ani

- Při spouštění aplikace zadejte **VSPerfCmd/LineOff \<other arguments>**.

## <a name="see-also"></a>Viz také
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
- [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)
