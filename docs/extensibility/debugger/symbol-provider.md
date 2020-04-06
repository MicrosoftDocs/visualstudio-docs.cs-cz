---
title: Poskytovatel symbolů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712810"
---
# <a name="symbol-provider"></a>Poskytovatel symbolů
Implementace vyhodnocení výrazu musí přistupovat k informacím o symbolickéladění generované kompilátorjazyka k vyhodnocení proměnných a výrazů. Činí tak tím, že spotřebovává rozhraní zprostředkovatele symbolu (SP), nazývaného také obslužná rutina symbolu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dodává sp pro spravovaný kód, stejně jako nativní kód pomocí programu DataBase (PDB) symbol souboru formátu. Pokud není nutné, aby program používal symboly uložené ve vlastním formátu, doporučujeme použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sp dodávané společností .

## <a name="implementation-notes"></a>Poznámky k implementaci
 Ladicí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moduly očekávají, že budou hovořit s s sp pomocí rozhraní CLR (Common Language Runtime). V důsledku toho sp, který bude pracovat s moduly ladění sady Visual Studio musí podporovat CLR. Kompletní seznam všech rozhraní ladění CLR naleznete v souboru debugref.doc, který [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]je součástí rozhraní .

 Pokud vaše SP bude pracovat pouze s vlastním ladicím strojem, můžete implementovat SP, jak uznáte za vhodné v závislosti na potřebách ladicího modulu.

## <a name="see-also"></a>Viz také
- [Součásti ladicího programu](../../extensibility/debugger/debugger-components.md)
