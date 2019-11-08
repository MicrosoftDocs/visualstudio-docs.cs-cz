---
title: 'Postupy: zobrazení dokumentů skriptu | Microsoft Docs'
ms.date: 11/05/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e362e0504c4ed2584bbbbea687fe3c58fc79edb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714437"
---
# <a name="how-to-view-script-documents-javascript"></a>Postupy: zobrazení dokumentů skriptu (JavaScript)

Soubory skriptu na straně serveru jsou viditelné v Průzkumník řešení. Soubory skriptu na straně klienta jsou viditelné pouze v režimu ladění nebo režimu přerušení. Soubory skriptu na straně klienta se zobrazí v uzlu **dokumenty skriptu** .

U některých typů aplikací, které dynamicky generují stránky, je snazší přejít do režimu přerušení a ladit při nastavení zarážky z dokumentu skriptu, který je načten v prohlížeči. Podobně můžete přidat příkaz `debugger` z načteného dokumentu skriptu pro přechod do režimu přerušení. V tomto článku se dozvíte, jak tyto dokumenty zobrazit.

> [!NOTE]
> Předchozí [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]se v okně Průzkumník skriptů objevily soubory skriptu na straně klienta generované ze skriptu na straně serveru.

### <a name="to-view-a-server-side-script-document"></a>Zobrazení dokumentu skriptu na straně serveru

1. V **Průzkumník řešení**otevřete uzel **\<Website cesta >** .

2. Dvakrát klikněte na soubor skriptu, který chcete zobrazit.

     V okně zdrojového kódu se otevře soubor skriptu na straně serveru.

### <a name="to-view-a-client-side-script-document"></a>Zobrazení dokumentu skriptu na straně klienta

1. V **Průzkumník řešení**otevřete uzel **dokumenty skriptu** .

2. Dvakrát klikněte na soubor skriptu, který chcete zobrazit.

     V okně zdrojového kódu se otevře soubor skriptu na straně klienta.

## <a name="see-also"></a>Viz také:
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)