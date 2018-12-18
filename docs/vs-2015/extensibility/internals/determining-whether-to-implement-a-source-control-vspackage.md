---
title: Určení, jestli se má implementovat VSPackage zdrojového ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18b7e24a246819b42b567d06cbcd556931f3244c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758016"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Určení toho, jestli se má implementovat balíček VSPackage správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato část popisuje možnosti řízení moduly plug-in zdrojového kódu a balíčků VSPackage správy zdrojového kódu pro rozšíření řešení a nabízí rozsáhlé pokyny o výběru cesty vhodné integrace správy zdrojového kódu.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Malé Source řešení pro ovládací prvek s omezenými zdroji  
 Pokud mají omezené prostředky a nemůže být burdened s nároky na zápis zdrojový ovládací prvek balíček, můžete vytvořit moduly plug-in založené na rozhraní API modulu Plug-in zdroje ovládacího prvku. Díky tomu můžete fungovat společně s balíčky správy zdrojového kódu a můžete přepínat mezi ovládací prvek moduly plug-in zdrojového kódu a balíčky na vyžádání. Další informace najdete v tématu [registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Řešení řízení velkých zdroje se sadou bohaté funkce  
 Pokud chcete implementovat řešení zdrojového ovládacího prvku, který poskytuje bohaté zdrojového ovládacího prvku modelu, který není dostatečně zachyceny pomocí rozhraní API modulu Plug-in zdroje ovládacího prvku, zvažte zdrojový balíček ovládací prvek jako cestu integrace. To platí zejména v případě, že místo toho by byly nahrazeny zdrojový balíček adaptér ovládací prvek (který komunikuje se ovládací prvek moduly plug-in zdrojového kódu a poskytuje základní zdroj ovládací prvek uživatelského rozhraní) s vlastním tak, aby bylo možné zpracovat události ovládacího prvku zdroje vlastní způsobem. Pokud už máte uspokojivé zdrojový ovládací prvek uživatelského rozhraní a chcete zachovat ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], možnosti správy zdrojového kódu balíček umožňuje udělat přesně takhle. Zdrojový ovládací prvek balíček není obecná a je určený výhradně pro použití s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí.  
  
 Pokud chcete implementovat řešení zdrojového ovládacího prvku, který poskytuje flexibilitu a lepší kontrolu nad zdrojového ovládacího prvku logiky a uživatelského rozhraní, možná dáte přednost zdrojového ovládacího prvku balíček integrace trasy. Můžeš:  
  
1.  Zaregistrovat vlastní ovládací prvek zdroje balíčku VSPackage (viz [registrace a výběr](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Nahraďte výchozí zdrojový ovládací prvek uživatelského rozhraní vlastního uživatelského rozhraní (viz [vlastní uživatelské rozhraní](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Zadejte glyfy použít a zpracovat události piktogram Průzkumníka řešení (viz [piktogramů](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Zpracování událostí dotazu upravit a uložit dotaz (viz [dotaz upravit dotaz uložit](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)

