---
title: Správa součástí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191854"
---
# <a name="component-management"></a>Správa komponent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jednotky úloh v Instalační služba systému Windows jsou označovány jako Instalační služba systému Windows komponenty (někdy označované jako WICs nebo pouze komponenty). Identifikátor GUID identifikuje každou součást WIC, což je základní jednotka instalace a počítání odkazů pro nastavení, která používají Instalační služba systému Windows.  
  
 I když můžete použít několik produktů k vytvoření instalačního programu sady VSPackage, Tato diskuze předpokládá použití souborů Instalační služba systému Windows (. msi). Při vytváření instalačního programu je nutné správně spravovat nasazení souboru, aby se vždy nastalo správný počet odkazů. V důsledku toho nebudou různé verze produktu v kombinaci scénářů instalace a odinstalace navzájem narušovat ani přerušovat.  
  
 V Instalační služba systému Windows probíhá počítání odkazů na úrovni komponenty. Své prostředky, soubory, položky registru a tak dále je nutné pečlivě uspořádat do komponent. Existují i další úrovně organizace, jako jsou moduly, funkce a produkty, které můžou pomáhat v různých scénářích. Další informace najdete v tématu [základy Instalační služba systému Windows](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Pokyny k vytváření nastavení pro souběžnou instalaci  
  
- Vytváření souborů a klíčů registru, které jsou sdíleny mezi verzemi, do jejich vlastních komponent.  
  
     To vám umožní je snadno využívat v další verzi. Například zadejte knihovny, které jsou registrovány globálně, přípony souborů, další položky zaregistrované v HKEY_CLASSES_ROOT atd.  
  
- Seskupte sdílené součásti do samostatných slučovacích modulů.  
  
     To vám pomůže vytvořit správně pro souběžné přesuny.  
  
- Nainstalujte sdílené soubory a klíče registru pomocí stejné Instalační služba systému Windows komponenty napříč verzemi.  
  
     Použijete-li jinou součást, soubory a položky registru se odinstalují, když se odinstaluje jedna verze VSPackage, ale je stále nainstalován jiný VSPackage.  
  
- Nepoužívejte kombinaci verzí a sdílených položek ve stejné součásti.  
  
     Díky tomu není možné instalovat sdílené položky do globálního umístění a z položek se správou verzí do izolovaných umístění.  
  
- Nemusíte mít sdílené klíče registru, které odkazují na soubory se správou verzí.  
  
     Pokud to uděláte, budou se sdílené klíče přepsat při instalaci další verze VSPackage. Po odebrání druhé verze se zobrazí soubor, na který se klíč odkazuje.  
  
## <a name="see-also"></a>Viz také  
 [Volba mezi sdílenými a sesprávou verzí VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scénáře instalace balíčku VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
