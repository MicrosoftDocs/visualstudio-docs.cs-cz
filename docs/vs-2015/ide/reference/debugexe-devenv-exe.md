---
title: -DebugExe (devenv.exe) | Dokumentace Microsoftu
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
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56ff98aa40e122b5067bd17d72334daf93164fe2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262649"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Otevře zadaný spustitelný soubor k ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Arguments  
 `ExecutableFile`  
 Požadováno. Název a cesta k souboru .exe.  
  
 Pokud soubor .exe se nenašel nebo neexistuje, je zobrazovat žádná upozornění ani chyby a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spustí běžným způsobem.  
  
## <a name="remarks"></a>Poznámky  
 Všechny řetězce po `ExecutableFile` parametru jsou předány do tohoto souboru jako argumenty.  
  
## <a name="example"></a>Příklad  
 Následující příklad otevře soubor `MyApplication.exe` pro ladění.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Viz také  
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)



