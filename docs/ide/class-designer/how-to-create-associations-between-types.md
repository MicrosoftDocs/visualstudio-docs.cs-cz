---
title: 'Postupy: vytvoření přidružení mezi typy (návrhář tříd)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b27530abeec1c01b5537fd91bfbe3e0e10448af
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958552"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Postupy: vytvoření přidružení mezi typy v Návrháři tříd

Přidružení řádků v **návrhář tříd** ukazují, jak jsou související třídy v diagramu. Asociační čára představuje třídu, která je typem vlastnosti nebo pole jiné třídy ve vašem projektu. Asociační čáry obecně slouží ke znázornění nejdůležitějších vztahů mezi třídami v projektu.

Ačkoli můžete zobrazit všechna pole a vlastnosti jako přidružení, je vhodnější jako přidružení zobrazit pouze důležité členy nebo přidružení v závislosti na tom, co chcete v diagramu zdůraznit. (Můžete zobrazit méně důležité členy jako běžné členy nebo je zcela skrýt.)

> [!NOTE]
> **Třídy návrháře** podporuje jenom jednosměrný přidružení.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Definování asociační čáry v diagramu tříd

1. V panelu nástrojů v části **návrhář tříd**, vyberte **přidružení**.

2. Nakreslete čáru mezi dvěma tvary, které chcete propojit pomocí přidružení.

     V první třídě se vytvoří nová vlastnost. Tato vlastnost se zobrazí jako asociační čára (nikoli jako vlastnost v prostoru ve tvaru) s výchozím názvem. Její typ je tvar, na který asociační čára ukazuje.

## <a name="to-change-the-name-of-an-association"></a>Změna názvu přidružení

Na ploše diagramu klikněte na popisek asociační linky a upravte jej.

Případně postupujte takto:

1. Vyberte obrazec, který obsahuje vlastnost, která se zobrazí jako přidružení.

   Tvar, který získá fokus a její členy zobrazit v **podrobností třídy** a **vlastnosti** systému windows.

2. Buď **podrobností třídy** nebo **vlastnosti** okně Upravit pole název pro tuto vlastnost a stiskněte klávesu **Enter**.

   Název se aktualizuje v **podrobností třídy** v okně na přidružení řádek **vlastnosti** okno a v kódu.

## <a name="see-also"></a>Viz také

- [Postupy: změna mezi zápisem člena a zápisem asociace](how-to-change-between-member-notation-and-association-notation.md)
