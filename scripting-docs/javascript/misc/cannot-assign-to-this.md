---
title: Nejde přiřadit k této | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73baa77cc63e3a43ac30e70f66081bbc7ade3020
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572349"
---
# <a name="cannot-assign-to-this"></a>Nelze přiřazovat do objektu 'this'
Pokusili jste se přiřadit hodnotu k **tomuto**. **Toto** je klíčové slovo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], které odkazuje na jednu z těchto akcí:

- objekt, který aktuálně provádí metodu,

- globální objekt, pokud neexistuje žádná aktuální metoda (nebo metoda nepatří do žádného jiného objektu).

Metoda je [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkce, která je vyvolána prostřednictvím objektu. V rámci metody je **Toto** klíčové slovo odkazem na objekt, na který byla metoda volána (což se stane objektem vytvořeným voláním konstruktoru třídy s operátorem **New** ).

V rámci metody můžete použít **tuto** možnost, chcete-li odkazovat na aktuální objekt, ale **nelze k němu**přiřadit novou hodnotu.

## <a name="to-correct-this-error"></a>Oprava této chyby

- Nepokoušejte se přiřadit k **tomuto**. Pro přístup k vlastnosti nebo metodě vytvořeného objektu použijte operátor tečka (například **Circle. RADIUS**).

  > [!NOTE]
  > **Tuto**proměnnou vytvořenou uživatelem nelze pojmenovat; je to [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] rezervované slovo.

## <a name="see-also"></a>Viz také:

- [this – příkaz](../../javascript/reference/this-statement-javascript.md)
- [Řešení potíží se skripty](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)