---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147099"
---
Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. Útok proti nezabezpečenému odserializaci může například provádět příkazy v podkladovém operačním systému, komunikovat přes síť nebo odstraňovat soubory.