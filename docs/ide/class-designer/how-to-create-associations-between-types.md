---
title: 'Postupy: Vytvoření asociací mezi typy (Návrhář tříd)'
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61b598505ad465ec9086102b9e16e96cb7aa8275
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590381"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Postup: Vytvoření přidružení mezi typy v Návrháři tříd

Řádky přidružení v **Návrháři tříd** ukazují, jak spolu souvisejí třídy v diagramu. Asociační čára představuje třídu, která je typem vlastnosti nebo pole jiné třídy ve vašem projektu. Asociační čáry obecně slouží ke znázornění nejdůležitějších vztahů mezi třídami v projektu.

Ačkoli můžete zobrazit všechna pole a vlastnosti jako přidružení, je vhodnější jako přidružení zobrazit pouze důležité členy nebo přidružení v závislosti na tom, co chcete v diagramu zdůraznit. (Můžete zobrazit méně důležité členy jako běžné členy nebo je zcela skrýt.)

> [!NOTE]
> **Návrhář třídpodporuje** pouze jednosměrná přidružení.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Definování asociační čáry v diagramu tříd

1. V panelu nástrojů vyberte v části **Návrhář třídmožnost** **IACe .**

2. Nakreslete čáru mezi dvěma tvary, které chcete propojit pomocí přidružení.

     V první třídě se vytvoří nová vlastnost. Tato vlastnost se zobrazí jako asociační čára (nikoli jako vlastnost v prostoru ve tvaru) s výchozím názvem. Její typ je tvar, na který asociační čára ukazuje.

## <a name="to-change-the-name-of-an-association"></a>Změna názvu přidružení

Na ploše diagramu klikněte na popisek asociační linky a upravte jej.

Případně postupujte takto:

1. Vyberte obrazec, který obsahuje vlastnost, která je zobrazena jako přidružení.

   Obrazec získá fokus a jeho členy se zobrazí v **oknech Podrobnosti a** **vlastnosti** třídy.

2. V okně **Podrobnosti třídy** nebo **Vlastnosti** upravte pole názvu této vlastnosti a stiskněte **Enter**.

   Název je aktualizován v okně **Podrobnosti třídy,** na řádku přidružení, v okně **Vlastnosti** a v kódu.

## <a name="see-also"></a>Viz také

- [Postup: Změna mezi zápisem člena a zápisem přidružení](how-to-change-between-member-notation-and-association-notation.md)
