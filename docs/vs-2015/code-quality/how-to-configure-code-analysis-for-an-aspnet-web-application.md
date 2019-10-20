---
title: 'Postupy: konfigurace analýzy kódu pro webovou aplikaci v ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657467"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Postupy: Konfigurace Analýzy kódu pro webovou aplikaci ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] a [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] můžete vybrat ze seznamu *sad pravidel* analýzy kódu, které se mají použít pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci. Výchozí sada pravidel je doporučená pravidla Microsoft Mininimum. Můžete vybrat jinou sadu pravidel, která se má použít na web.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Konfigurace sady pravidel pro projekt architektury stránky ASP.NET

1. Vyberte web v **Průzkumník řešení**.

2. V nabídce **analyzovat** klikněte na položku **Konfigurovat analýzu kódu pro web**.

3. Pokud jste vybrali řešení a řešení obsahuje více než jeden projekt, vyberte konfigurace sestavení a cílový operační systém v seznamech **Konfigurace** a **platforma** .

4. Pro každý projekt v řešení klikněte na sloupec **sada pravidel** a potom klikněte na název sady pravidel ke spuštění.

5. Ve výchozím nastavení se analýza kódu spouští na všech projektech v řešení. Chcete-li zakázat nebo povolit analýzu kódu pro určitý projekt, postupujte takto:

    1. Klikněte pravým tlačítkem myši na název projektu a pak klikněte na vlastnosti.

    2. Zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit analýzu kódu** . Analýzu kódu lze také spustit ručně výběrem možnosti **Spustit analýzu kódu na** webu v nabídce **analyzovat** .

6. V rozevíracím seznamu **Spustit tuto sadu pravidel** proveďte tyto kroky:

    - Vyberte sadu pravidel, kterou chcete použít.

    - Vyberte **\<Browse >** a zadejte existující vlastní sadu pravidel, která není v seznamu.

    - Definujte vlastní sadu pravidel. Další informace najdete v tématu [vytváření vlastních sad pravidel](../code-quality/creating-custom-code-analysis-rule-sets.md).
