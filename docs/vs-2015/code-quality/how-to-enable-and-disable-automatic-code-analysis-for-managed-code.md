---
title: 'Postupy: povolení a zákaz automatické analýzy kódu pro spravovaný kód | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d87cc57b31e63ae7aafa53c335df2b56f86a0409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658100"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Postupy: Povolení a zákaz automatické analýzy kódu pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Je možné konfigurovat analýzu kódu pro spuštění před každým sestavením spravovaného kódu projektu. Pro každou konfiguraci můžete nastavit různé vlastnosti analýzy kódu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

### <a name="to-enable-or-disable-automatic-code-analysis"></a>Povolení nebo zakázání automatické analýzy kódu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak klikněte na **vlastnosti**.

2. V dialogovém okně Vlastnosti projektu klikněte na možnost **Analýza kódu**.

3. Zadejte typ sestavení v **konfiguraci** a cílovou platformu na **platformě**.

4. Chcete-li povolit nebo zakázat automatickou analýzu kódu, zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit analýzu kódu při sestavení (definuje CODE_ANALYSIS konstanta)** .
