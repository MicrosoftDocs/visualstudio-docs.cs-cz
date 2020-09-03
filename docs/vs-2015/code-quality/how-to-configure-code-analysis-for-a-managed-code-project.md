---
title: 'Postupy: konfigurace analýzy kódu pro projekt spravovaného kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658846"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Postupy: Konfigurace Analýzy kódu pro spravovaný projekt kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] systému a [!INCLUDE[vsPro](../includes/vspro-md.md)] můžete zvolit ze seznamu *sad pravidel* analýzy kódu, které se mají použít pro projekt spravovaného kódu. Výchozí sada pravidel je minimální doporučená pravidla společnosti Microsoft. Můžete použít jinou sadu pravidel na projekt nebo pro všechny projekty v řešení.

> [!NOTE]
> Informace o tom, jak nakonfigurovat sadu pravidel pro webové aplikace v ASP.NET, naleznete v tématu [How to: Configure Code Analysis for the ASP.NET Web Application](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Konfigurace sady pravidel pro .NET Framework projekt

1. V **Průzkumník řešení**klikněte na projekt.

2. V nabídce **analyzovat** klikněte na položku **Konfigurovat analýzu kódu pro** *ProjectName*.

3. V seznamech **Konfigurace** a **platforma** klikněte na položku konfigurace sestavení a cílová platforma.

4. Chcete-li spustit analýzu kódu pokaždé, když je projekt sestaven pomocí vybrané konfigurace, vyberte zaškrtávací políčko **Povolit analýzu kódu při sestavení (definuje CODE_ANALYSIS konstanta)** . Analýzu kódu lze také spustit ručně otevřením nabídky **analyzovat** a kliknutím na možnost **Spustit analýzu kódu v** *ProjectName*.

5. Ve výchozím nastavení nástroj Code Analysis nehlásí upozornění z kódu, který je automaticky generován externími nástroji. Chcete-li zobrazit upozornění z vygenerovaného kódu, zrušte zaškrtnutí políčka **Potlačit výsledky z vygenerovaného kódu** .

    > [!NOTE]
    > Tato možnost potlačí chyby a upozornění analýzy kódu z generovaného kódu, pokud se chyby a upozornění zobrazují ve formulářích a šablonách. Zdrojový kód formuláře nebo šablony můžete zobrazit a spravovat.

6. V seznamu **Spustit tuto sadu pravidel** proveďte jednu z následujících akcí:

    - Klikněte na sadu pravidel, kterou chcete použít.

    - Kliknutím **\<Browse...>** můžete zadat existující sadu vlastních pravidel, která není v seznamu.

    - Definujte vlastní sadu pravidel.

         Další informace najdete v tématu [vytváření vlastních sad pravidel](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Viz také
 [Návod: Konfigurace a používání vlastní sady pravidel](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
