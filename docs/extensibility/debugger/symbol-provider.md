---
title: Zprostředkovatel symbolů | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712810"
---
# <a name="symbol-provider"></a>Zprostředkovatel symbolů
Implementace vyhodnocovacího filtru výrazů musí přistupovat k symbolickým ladicím informacím generovaným kompilátorem jazyka, aby bylo možné vyhodnotit proměnné a výrazy. Udělá to tak, že zabírají rozhraní zprostředkovatele symbolů (SP), označovaného také jako obslužná rutina symbolu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje SPs pro spravovaný kód i nativní kód pomocí formátu souboru symbolů databáze programu (PDB). Pokud nepotřebujete, aby váš program používal symboly uložené ve vlastním formátu, doporučuje se použít služby SPs dodávané nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Poznámky k implementaci
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ladicí stroje od verze modulu CLR (Common Language Runtime) očekávají, že mluví se službou SPS. V důsledku toho musí být v rámci SP, který bude pracovat s ladicími moduly sady Visual Studio, podporován modul CLR. Úplný seznam všech rozhraní ladění CLR najdete v debugref.doc, který je součástí [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Pokud bude vaše aktualizace SP fungovat jenom s vaším vlastním ladicím modulem, můžete implementovat SP podle toho, jak se bude zobrazovat podle potřeb vašeho ladicího stroje.

## <a name="see-also"></a>Viz také
- [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
