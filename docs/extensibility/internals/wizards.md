---
title: Kouzelníci | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703210"
---
# <a name="wizards"></a>Průvodci
Po vytvoření průvodce jej obvykle chcete přidat do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE), aby jej ostatní mohli používat. Přidaný průvodce se pak zobrazí v dialogových oknech **Přidat nový projekt** nebo Přidat novou **položku.** Pokud chcete zobrazit dialogová okna **Přidat nový projekt** nebo Přidat novou **položku,** klikněte pravým tlačítkem myši na otevřené řešení v **Průzkumníku řešení**, přejděte na **Přidat**a potom klikněte na **Nový projekt** nebo **Nová položka**.

 Průvodci mohou být [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementováni v aplikaci, aby uživatelé mohli vybírat ze stromového zobrazení dostupných hodnot při otevření dialogového okna **Přidat nový projekt** nebo dialogového okna Přidat novou **položku** nebo když klepnou pravým tlačítkem myši na položku v **Průzkumníku řešení**.

 V průvodci můžete zadat možnost lokalizovat název nového projektu nebo ites a můžete určit ikonu, kterou uživatelé uvidí při výběru průvodce. Můžete také řídit pořadí, ve kterém se nové položky zobrazují vzhledem k ostatním dostupným položkám; položky nemusí být uspořádány abecedně.

 Můžete také zadat průvodce, který se spustí odlišně, na základě vlastních parametrů, které jsou předány průvodci při jeho otevření.

 Témata v této části popisují soubory, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementujete, aby dialogové okna **Přidat nový projekt** a Přidat novou **položku** uvedeprůvodce mezi dostupnými průvodci a šablonami a požadavky, které musí průvodce splňovat, aby v prostředí IDE fungoval správně.

## <a name="in-this-section"></a>V tomto oddílu
- [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Poskytuje přehled souborů s popisem adresáře šablony a vysvětluje, jak fungují v prostředí IDE pro zobrazení složek, souborů průvodce .vsz a souborů šablon, které jsou přidruženy k projektu v dialogových oknech.

- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Vysvětluje, jak rozhraní IDE spustí průvodce a uvádí tři části souboru .vsz.

- [Rozhraní průvodce (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Popisuje `IDTWizard` rozhraní, které musí průvodci implementovat, aby fungovalo v rozhraní IDE.

- [Parametry kontextu](../../extensibility/internals/context-parameters.md)

 Vysvětluje, jak jsou implementováni průvodci a co nastane, když rozhraní IDE předá parametry kontextu do implementace.

- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)

 Vysvětluje, jak používat vlastní parametry k řízení operace průvodce po spuštění průvodce.

## <a name="related-sections"></a>Související oddíly
- [Typy projektů](../../extensibility/internals/project-types.md)

 Obsahuje odkazy na další témata, která nabízejí informace o tom, jak navrhnout nové typy projektů.

- [Rozšíření projektů](../../extensibility/extending-projects.md)

 Popisuje použití [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektů a řešení k uspořádání souborů kódu a souborů prostředků a jak implementovat správu zdrojového kódu.
