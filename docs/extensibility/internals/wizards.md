---
title: Průvodci | Microsoft Docs
description: Naučte se, jak vypsat průvodce mezi dostupnými průvodci a šablonami v aplikaci Visual Studio a o požadavcích, které váš průvodce musí splnit v integrovaném vývojovém prostředí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 828a08cfe2841595e0ed3a9f1e3d79973a6e6756
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943378"
---
# <a name="wizards"></a>Průvodci
Po vytvoření průvodce je obvykle vhodné ho přidat do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE), aby ho ostatní mohli používat. Přidaný průvodce se pak zobrazí v dialogových oknech **Přidat nový projekt** nebo **Přidat novou položku** . Chcete-li zobrazit dialogová okna **Přidat nový projekt** nebo **Přidat novou položku** , klikněte pravým tlačítkem myši na otevřené řešení v **Průzkumník řešení**, přejděte na **Přidat** a pak klikněte na **Nový projekt** nebo **Nová položka**.

 Průvodci mohou být implementováni v aplikaci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , aby uživatelům při otevření dialogového okna **Přidat nový projekt** nebo **Přidat novou položku** nebo po kliknutí pravým tlačítkem myši na položku v **Průzkumník řešení** vybrali ze stromového zobrazení dostupných hodnot.

 V průvodci můžete zadat možnost lokalizace názvu nového projektu nebo ITES a můžete určit ikonu, kterou uživatelé uvidí při výběru průvodce. Můžete také řídit pořadí, ve kterém se nové položky zobrazují relativně k ostatním dostupným položkám; položky nemusejí být uspořádány abecedně.

 Můžete také dodávat průvodce, který se spouští jinak, na základě vlastních parametrů, které se předávají průvodci při jeho otevření.

 Témata v této části popisují soubory, které implementujete k tomu, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dialogová okna **Přidat nový projekt** a **Přidat novou položku** zobrazovala průvodce v rámci dostupných průvodců a šablon a požadavky, které průvodce musí splňovat, aby správně fungoval v integrovaném vývojovém prostředí (IDE).

## <a name="in-this-section"></a>V tomto oddílu
- [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Poskytuje přehled o tom, které soubory popisu adresáře šablon a vysvětluje, jak fungují v integrovaném vývojovém prostředí pro zobrazení složek, souborů Průvodce. vsz a souborů šablon, které jsou přidruženy k projektu v dialogových oknech.

- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Vysvětluje, jak IDE spustí průvodce a uvádí tři části souboru. vsz.

- [Rozhraní průvodce (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Popisuje `IDTWizard` rozhraní, které průvodci musí implementovat pro práci v integrovaném vývojovém prostředí (IDE).

- [Kontextové parametry](../../extensibility/internals/context-parameters.md)

 Vysvětluje, jak jsou implementovány průvodci a co se stane, když rozhraní IDE předá implementaci kontextových parametrů.

- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)

 Vysvětluje způsob použití vlastních parametrů k řízení činnosti průvodce po spuštění průvodce.

## <a name="related-sections"></a>Související oddíly
- [Typy projektů](../../extensibility/internals/project-types.md)

 Obsahuje odkazy na další témata, která nabízejí informace o návrhu nových typů projektů.

- [Rozšíření projektů](../../extensibility/extending-projects.md)

 Popisuje, jak používat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty a řešení k uspořádání souborů kódu a souborů prostředků a jak implementovat správu zdrojového kódu.
