---
title: Začínáme s plug-in zdroje ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2f1eb4f76616f6a5f6791cbcd1b8a5770d1dcabb
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498097"
---
# <a name="get-started-with-source-control-plug-ins"></a>Začínáme s plug-in zdroje ovládacího prvku
Chcete-li vytvořit modul plug-in správy zdrojového kódu, musíte vytvořit knihovnu DLL, která implementuje funkce definované v rozhraní API modulu Plug-in zdroje ovládacího prvku a následně registrace knihovny DLL s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aby byl k dispozici pro použití v správy verze zdrojového kódu.  
  
 Tři verze rozhraní API modulu Plug-in zdroje ovládacího prvku (verze 1.1, 1.2 a 1.3) jsou k dispozici pro ovládací prvek moduly plug-in zdrojového kódu. Rozhraní API modulu Plug-in zdroje ovládacího prvku zdokumentované tady je verze 1.3. Jejím účelem je plně kompatibilní s ovládací prvek moduly plug-in zdrojového kódu podporující verze 1.1 a 1.2. [Co je nového ve verzi 1.3 zdroj ovládacího prvku modulu Plug-in API](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) část podrobně popisuje nové funkce podporované v nejnovější verzi rozhraní API modulu Plug-in zdroje ovládacího prvku.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Instalace modulu plug-in správy zdrojového kódu](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Popisuje, jak vytvořit položky registru, které jsou nutné k modulu plug-in správy zdrojového kódu knihovny DLL.  
  
 [Co je nového ve verzi 1.3 zdrojový ovládací prvek modulu Plug-in rozhraní API](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Poskytuje stručný přehled o změny, které byly provedeny API modulu Plug-in zdroje ovládacího prvku ve verzi 1.3.  
  
 [Co je nového v zdrojový ovládací prvek modulu Plug-in API verze 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Poskytuje stručný přehled o změny, které byly provedeny u rozhraní API pro modul Plug-in zdroje ovládacího prvku ve verzi 1.2.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ovládací prvek moduly plug-in zdrojového kódu](../../extensibility/source-control-plug-ins.md)  
 Obsahuje úplný seznam všech prvků v rozhraní API modulu Plug-in zdroje ovládacího prvku.  
  
 [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definuje ovládací prvek modulu Plug-in Source sad SDK a popisuje zahrnuté prostředky.