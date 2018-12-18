---
title: -Updateconfiguration (devenv.exe) | Dokumentace Microsoftu
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
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ed69bf8c54d3b428907b4dbe0636f2966254de75
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253629"
---
# <a name="updateconfiguration-devenvexe"></a>/ Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Upozorní [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sloučit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mezipaměť balíčků na systém a rozhraní MEF pro všechny změny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tento příkaz se spustí automaticky při instalaci balíčku VSIX. Měli byste spustit `devenv.exe /updateconfiguration` po použití dílčích oprav soubory tak, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aktualizuje mezipaměť MEF. To umožňuje vyhodnotit, jestli je vhodná, jste kód opravili správně.  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek příčiny [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sloučit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mezipaměť balíčků na systém a rozhraní MEF pro všechny změny.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)



