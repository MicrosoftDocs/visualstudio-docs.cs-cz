---
title: Průvodci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e58ebd736f7bb9f35df6e41d5235f36f7037259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687619"
---
# <a name="wizards"></a>Průvodci
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po vytvoření průvodce je obvykle vhodné ho přidat do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE), aby ho ostatní mohli používat. Přidaný průvodce se pak zobrazí v dialogových oknech **Přidat nový projekt** nebo **Přidat novou položku** . Chcete-li zobrazit dialogová okna **Přidat nový projekt** nebo **Přidat novou položku** , klikněte pravým tlačítkem myši na otevřené řešení v **Průzkumník řešení**, přejděte na **Přidat**a pak klikněte na **Nový projekt** nebo **Nová položka**.  
  
 Průvodci mohou být implementováni v aplikaci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , aby uživatelům při otevření dialogového okna **Přidat nový projekt** nebo **Přidat novou položku** nebo po kliknutí pravým tlačítkem myši na položku v **Průzkumník řešení**vybrali ze stromového zobrazení dostupných hodnot.  
  
 V průvodci můžete zadat možnost lokalizace názvu nového projektu nebo ITES a můžete určit ikonu, kterou uživatelé uvidí při výběru průvodce. Můžete také řídit pořadí, ve kterém se nové položky zobrazují relativně k ostatním dostupným položkám; položky nemusejí být uspořádány abecedně.  
  
 Můžete také dodávat průvodce, který se spouští jinak, na základě vlastních parametrů, které se předávají průvodci při jeho otevření.  
  
 Témata v této části popisují soubory, které implementujete k tomu, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dialogová okna **Přidat nový projekt** a **Přidat novou položku** zobrazovala průvodce v rámci dostupných průvodců a šablon a požadavky, které průvodce musí splňovat, aby správně fungoval v integrovaném vývojovém prostředí (IDE).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Poskytuje přehled o tom, které soubory popisu adresáře šablon a vysvětluje, jak fungují v integrovaném vývojovém prostředí pro zobrazení složek, souborů Průvodce. vsz a souborů šablon, které jsou přidruženy k projektu v dialogových oknech.  
  
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Vysvětluje, jak IDE spustí průvodce a uvádí tři části souboru. vsz.  
  
 [Rozhraní průvodce (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Popisuje `IDTWizard` rozhraní, které průvodci musí implementovat pro práci v integrovaném vývojovém prostředí (IDE).  
  
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)  
 Vysvětluje, jak jsou implementovány průvodci a co se stane, když rozhraní IDE předá implementaci kontextových parametrů.  
  
 [Vlastní parametry](../../extensibility/internals/custom-parameters.md)  
 Vysvětluje způsob použití vlastních parametrů k řízení činnosti průvodce po spuštění průvodce.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Obsahuje odkazy na další témata, která nabízejí informace o návrhu nových typů projektů.  
  
 [Návod: vytvoření průvodce](https://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Ukazuje, jak vytvořit průvodce.  
  
 [Rozšíření projektů](../../extensibility/extending-projects.md)  
 Popisuje, jak používat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekty a řešení k uspořádání souborů kódu a souborů prostředků a jak implementovat správu zdrojového kódu.
