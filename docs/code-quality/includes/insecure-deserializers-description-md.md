---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89326215"
---
Nezabezpečené deserializace jsou zranitelné při deserializaci nedůvěryhodných dat. Útočník by mohl upravit Serializovaná data tak, aby zahrnovala neočekávané typy pro vložení objektů se škodlivými vedlejšími účinky. Útok proti nezabezpečenému odserializaci může například provádět příkazy v podkladovém operačním systému, komunikovat přes síť nebo odstraňovat soubory.