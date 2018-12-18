---
title: Správa komponent | Dokumentace Microsoftu
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
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 626717ed559257d04cb0bbcca3c76283aac22d63
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743303"
---
# <a name="component-management"></a>Správa komponent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jednotky úloh v instalačním programu sady Windows se označují jako součásti Instalační služby systému Windows (říká se jim WICs nebo pouze komponenty). Identifikátor GUID identifikuje každý WIC, což je základní jednotkou instalace a pro nastavení, která pomocí Instalační služby systému Windows pro počítání odkazů.  
  
 I když několik produktů slouží k vytvoření balíčku VSPackage instalační program, tento postup předpokládá použití souborů Instalační služby systému Windows (.msi). Při vytváření instalační program, musíte správně spravovat nasazení souborů tak, aby správné počítání se stane po celou dobu. V důsledku toho různé verze produktu nebude rušit nebo rozdělit mezi sebou v kombinaci instalace a odinstalace scénáře.  
  
 V instalačním programu Windows počítání odkazů dochází na úrovni součásti. Musíte pečlivě uspořádání prostředků – soubory, položky registru a tak dále, do komponenty. Existují další úrovně organizace, jako jsou moduly, funkce a produkty –, které mohou pomoci v různých scénářích. Další informace najdete v tématu [základy Instalační služby systému Windows](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Pokyny k vytváření nastavení pro instalaci vedle sebe  
  
-   Autor soubory a klíče registru, které jsou odkazy sdíleny mezi verzí do jejich vlastních složek.  
  
     To umožňuje snadno je můžou využívat v budoucí verzi. Knihovny typů, které jsou registrovány globálně, například souboru rozšíření, další položky, registrované v HKEY_CLASSES_ROOT a tak dále.  
  
-   Sdílené součásti pro seskupení samostatné slučovací moduly.  
  
     To pomáhá Autor správně pro side-by-side v budoucnu.  
  
-   Nainstalujte sdíleným souborům a klíčům registru pomocí stejné komponenty Instalační služby systému Windows ve verzích.  
  
     Pokud používáte jiné součásti, soubory a položky registru jsou odinstalovat, pokud jeden označené verzí balíčku VSPackage je odinstalována, ale jiné VSPackage je nainstalovaná.  
  
-   Nekombinujte čísly verzí a sdílené položky pod stejnou komponentou.  
  
     To znemožňuje nainstalovat do globální umístění a verzované položky, které chcete izolované umístění sdílené položky.  
  
-   Není nutné klíče sdíleného registru, které odkazují na soubory označené verzí.  
  
     Pokud tak učiníte, při instalaci jinou verzí balíčku VSPackage se přepíše sdílené klíče. Po odebrání druhou verzi souboru, ke kterému bude ukazovat klíč je pryč.  
  
## <a name="see-also"></a>Viz také  
 [Volba mezi sdíleným a Verzovaným rozšířením VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scénáře instalace balíčku VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

