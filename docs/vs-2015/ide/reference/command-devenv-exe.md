---
title: -– Příkaz (devenv.exe) | Dokumentace Microsoftu
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
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5f95d8758da77f1b720f0a1b6ca74f7ac753d805
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254365"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Provede zadaný příkaz po spuštění [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Arguments  
 `CommandName`  
 Požadováno. Úplný název [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkaz nebo jeho alias uzavřený v dvojitých uvozovkách. Další informace o syntaxi příkazů a aliasů naleznete v tématu [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Poznámky  
 Po dokončení spuštění IDE spustí pojmenovaný příkaz. Pokud použijete tento přepínač, rozhraní IDE nezobrazí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] úvodní stránku při spuštění.  
  
 Pokud doplněk vystavuje příkaz, můžete použít tento přepínač se spustit doplněk z příkazového řádku. Další informace najdete v tématu [postupy: řízení doplňků pomocí Správce doplňků](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Příklad  
 Tento příklad spustí aplikaci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a automaticky spustí makro otevřít oblíbené soubory.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Viz také  
 [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



