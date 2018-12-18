---
title: Nelze přiřadit k &#39;to&#39; | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47e55d39e85675b37d2ac9741d1207a9e81d369e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856643"
---
# <a name="cannot-assign-to-39this39"></a>Nelze přiřadit k &#39;to&#39;
Pokusili jste se přiřadit hodnotu **to**. **to** je [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] – klíčové slovo, který odkazuje na buď:

- objekt aktuálně provádění metody,

- globální objekt, pokud neexistuje žádná metoda aktuální (nebo metoda nepatří do jiného objektu).

Metoda je [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkci, která prostřednictvím objektu, který je vyvolána. Uvnitř metody **to** – klíčové slovo je odkaz na objekt vyvolání metody prostřednictvím (Probíhá bude objekt vytvořený pomocí volání konstruktoru třídy s **nové** operátor).

Uvnitř metody, můžete použít **to** k odkazování na aktuální objekt, ale nelze přiřadit novou hodnotu **to**.

## <a name="to-correct-this-error"></a>Oprava této chyby

- Nepokoušejte se přiřadit **to**. Pro přístup k vlastnosti nebo metody instance objektu, pomocí operátoru tečka (například **circle.radius**).

  > [!NOTE]
  > Nelze pojmenovat proměnnou uživatel vytvořil **to**; je [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] vyhrazené slovo.

## <a name="see-also"></a>Viz také

- [this – příkaz](../../javascript/reference/this-statement-javascript.md)
- [Řešení potíží se skripty](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)