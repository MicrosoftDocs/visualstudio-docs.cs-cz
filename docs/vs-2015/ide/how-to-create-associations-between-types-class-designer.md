---
title: 'Postupy: vytváření asociací mezi typy (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb46d3bf7096d0a7e14ce3926514d946d7536e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668119"
---
# <a name="how-to-create-associations-between-types-class-designer"></a>Postupy: Vytvoření asociací mezi typy (Návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Asociační čáry v Návrháři tříd zobrazují vztah tříd v diagramu. Asociační čára představuje třídu, která je typem vlastnosti nebo pole jiné třídy ve vašem projektu. Asociační čáry obecně slouží ke znázornění nejdůležitějších vztahů mezi třídami v projektu.

 Ačkoli můžete zobrazit všechna pole a vlastnosti jako přidružení, je vhodnější jako přidružení zobrazit pouze důležité členy nebo přidružení v závislosti na tom, co chcete v diagramu zdůraznit. (Můžete zobrazit méně důležité členy jako běžné členy nebo je zcela skrýt.)

> [!NOTE]
> Návrhář tříd podporuje pouze jednosměrná přidružení.

### <a name="to-define-an-association-line-in-the-class-diagram"></a>Definování asociační čáry v diagramu tříd

1. V sadě nástrojů vyberte v části Návrhář tříd možnost **asociace**.

2. Nakreslete čáru mezi dvěma tvary, které chcete propojit pomocí přidružení.

     V první třídě se vytvoří nová vlastnost. Tato vlastnost se zobrazí jako asociační čára (nikoli jako vlastnost v prostoru ve tvaru) s výchozím názvem. Její typ je tvar, na který asociační čára ukazuje.

### <a name="to-change-the-name-of-an-association"></a>Změna názvu přidružení

- Na ploše diagramu klikněte na popisek asociační linky a upravte jej.

  \- ani

1. Klikněte na tvar, který obsahuje vlastnost zobrazenou jako přidružení.

     Tvar získá fokus a jeho členy se zobrazí v okně Detaily třídy a v okně Vlastnosti.

2. V okně Detaily třídy, nebo v okně Vlastnosti upravte pole názvu vlastnosti a stiskněte klávesu Enter.

     Název se aktualizuje v okně **podrobností třídy** , na čáře přidružení, v okno Vlastnosti a v kódu.

## <a name="see-also"></a>Viz také
 [Postupy: Změna mezi zápisem člena a zápisem asociace (návrhář tříd)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)
