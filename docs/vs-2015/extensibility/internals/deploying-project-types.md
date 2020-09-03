---
title: Nasazení typů projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196883"
---
# <a name="deploying-project-types"></a>Nasazování typů projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] nainstaluje nový agregátor typu projektu (ProjectAggregator2.dll) a také Instalační služba systému Windows balíček pro redistribuci (ProjectAggregator2.msi). Je nutné použít nový agregátor pro typy projektů spravovaného kódu. ProjectAggregator2 pracuje s omezeními v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Agregátoru projektu, který brání správnému fungování typů projektů spravovaného kódu. Následující postup popisuje, jak změnit VSPackage na použití nového Agregátoru.  
  
1. Odeberte projekt NativeHierarchyWrapper z vašeho řešení.  
  
2. Z instalačního programu odeberte všechny binární soubory NativeHierarchyWrapper.  
  
3. Přidejte ProjectAggregator2.msi k instalaci.
