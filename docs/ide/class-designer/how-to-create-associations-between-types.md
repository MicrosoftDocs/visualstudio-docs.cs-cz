---
title: 'Postupy: Vytvoření asociací mezi typy (Návrhář tříd)'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cce893efaad5f2317b175391a2685cae7053e3c
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770959"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Postupy: vytváření přidružení mezi typy v Návrhář tříd

Asociační čáry v **Návrhář tříd** ukazují, jak se třídy v diagramu vztahují. Asociační čára představuje třídu, která je typem vlastnosti nebo pole jiné třídy ve vašem projektu. Asociační čáry obecně slouží ke znázornění nejdůležitějších vztahů mezi třídami v projektu.

Ačkoli můžete zobrazit všechna pole a vlastnosti jako přidružení, je vhodnější jako přidružení zobrazit pouze důležité členy nebo přidružení v závislosti na tom, co chcete v diagramu zdůraznit. (Můžete zobrazit méně důležité členy jako běžné členy nebo je zcela skrýt.)

> [!NOTE]
> **Návrhář tříd** podporuje pouze jednosměrná přidružení.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Definování asociační čáry v diagramu tříd

1. V sadě nástrojů vyberte v části **Návrhář tříd**možnost **asociace**.

2. Nakreslete čáru mezi dvěma tvary, které chcete propojit pomocí přidružení.

     V první třídě se vytvoří nová vlastnost. Tato vlastnost se zobrazí jako asociační čára (nikoli jako vlastnost v prostoru ve tvaru) s výchozím názvem. Její typ je tvar, na který asociační čára ukazuje.

## <a name="to-change-the-name-of-an-association"></a>Změna názvu přidružení

Na ploše diagramu klikněte na popisek asociační linky a upravte jej.

Případně použijte následující postup:

1. Vyberte tvar, který obsahuje vlastnost, která se zobrazuje jako přidružení.

   Obrazec získá fokus a jeho členové se zobrazí v oknech **Podrobnosti třídy** a **vlastnosti** .

2. V okně **Podrobnosti třídy** nebo **vlastnosti** upravte pole název pro danou vlastnost a stiskněte klávesu **ENTER**.

   Název se aktualizuje v okně **podrobností třídy** , na čáře přidružení, v okně **vlastnosti** a v kódu.

## <a name="see-also"></a>Viz také:

- [Postupy: Změna mezi zápisem člena a zápisem přidružení](how-to-change-between-member-notation-and-association-notation.md)
