---
title: Postup zobrazení dokumentů skriptu | Microsoft Docs
ms.date: 11/05/2019
ms.topic: how-to
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
ms.openlocfilehash: dcd9823e414005a1711ddccf9d972da929090920
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348441"
---
# <a name="how-to-view-script-documents-javascript"></a>Postupy: zobrazení dokumentů skriptu (JavaScript)

Soubory skriptu na straně serveru jsou viditelné v Průzkumník řešení. Soubory skriptu na straně klienta jsou viditelné pouze v režimu ladění nebo režimu přerušení. Soubory skriptu na straně klienta se zobrazí v uzlu **dokumenty skriptu** .

U některých typů aplikací, které dynamicky generují stránky, je snazší přejít do režimu přerušení a ladit při nastavení zarážky z dokumentu skriptu, který je načten v prohlížeči. Podobně můžete přidat `debugger` příkaz z načteného dokumentu skriptu pro přechod do režimu přerušení. V tomto článku se dozvíte, jak tyto dokumenty zobrazit.

> [!NOTE]
> Předchozí se [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] soubory skriptu na straně klienta generované ze skriptu na straně serveru se objevily v okně Průzkumník skriptů.

### <a name="to-view-a-server-side-script-document"></a>Zobrazení dokumentu skriptu na straně serveru

1. V **Průzkumník řešení**otevřete **\<Website Pathname>** uzel.

2. Dvakrát klikněte na soubor skriptu, který chcete zobrazit.

     V okně zdrojového kódu se otevře soubor skriptu na straně serveru.

### <a name="to-view-a-client-side-script-document"></a>Zobrazení dokumentu skriptu na straně klienta

1. V **Průzkumník řešení**otevřete uzel **dokumenty skriptu** .

2. Dvakrát klikněte na soubor skriptu, který chcete zobrazit.

     V okně zdrojového kódu se otevře soubor skriptu na straně klienta.

## <a name="see-also"></a>Viz také
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)