---
title: -Command (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9083d14c82eb2d283431e28d03bbbf96c14258cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660859"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spustí zadaný příkaz po spuštění integrovaného vývojového prostředí (IDE) [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Syntaxe

```
devenv /command CommandName
```

## <a name="arguments"></a>Arguments
 `CommandName` nutné. Úplný název [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ho příkazu nebo jeho aliasu uzavřený do dvojitých uvozovek. Další informace o syntaxi příkazu a aliasu naleznete v tématu [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Poznámky
 Po dokončení spuštění IDE spustí pojmenovaný příkaz. Pokud použijete tento přepínač, rozhraní IDE při spuštění nezobrazí úvodní stránku [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Pokud doplněk zpřístupňuje příkaz, můžete pomocí tohoto přepínače spustit doplněk z příkazového řádku. Další informace najdete v tématu [Postup: ovládání doplňků pomocí Správce doplňků](https://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Příklad
 Tento příklad spustí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a automaticky spustí makro otevření oblíbených souborů.

```
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Viz také
 [Parametry příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) – [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
