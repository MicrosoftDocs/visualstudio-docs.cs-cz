---
title: -LCID (devenv.exe) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 242e0055e59312cba616859e08a2a61a45064e66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301909"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Nastaví výchozí jazyk používaný pro text, měny a jiné hodnoty v rámci integrovaného vývojového prostředí (IDE).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Arguments  
 `LocaleID`  
 Požadováno. Identifikátor LCID (ID národního prostředí) jazyka, který zadáte.  
  
## <a name="remarks"></a>Poznámky  
 Načte integrovaného vývojového prostředí a nastaví výchozí přirozeného jazyka pro prostředí. Tato změna je trvalá mezi relacemi a projeví na **mezinárodní nastavení** podokně **prostředí** možnosti **možnosti** dialogového okna v rozhraní IDE.  
  
 Pokud zadaný jazyk není k dispozici v systému uživatele, přepínač/LCID je ignorován.  
  
 V následující tabulce jsou uvedeny LCID jazyky podporovanými [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Jazyk|LCID|  
|--------------|----------|  
|Čínština (zjednodušená)|2052|  
|Čínština (tradiční)|1028|  
|Angličtina|1033|  
|Francouzština|1036|  
|Němčina|1031|  
|Italština|1040|  
|Japonština|1041|  
|Korejština|1042|  
|Španělština|3082|  
  
## <a name="example"></a>Příklad  
 Tento příklad načte integrované vývojové prostředí s anglickou prostředky řetězců.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>Viz také  
 [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Mezinárodní nastavení, prostředí, dialogové okno Možnosti](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)



