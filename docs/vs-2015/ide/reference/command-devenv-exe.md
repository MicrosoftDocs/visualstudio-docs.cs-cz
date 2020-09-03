---
title: -Command (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660859"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spustí zadaný příkaz po spuštění [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```
devenv /command CommandName
```

## <a name="arguments"></a>Argumenty
 `CommandName` Požadovanou. Úplný název [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkazu nebo jeho alias uzavřený do dvojitých uvozovek. Další informace o syntaxi příkazu a aliasu naleznete v tématu [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Poznámky
 Po dokončení spuštění IDE spustí pojmenovaný příkaz. Pokud použijete tento přepínač, rozhraní IDE nezobrazuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] úvodní stránku při spuštění.

 Pokud doplněk zpřístupňuje příkaz, můžete pomocí tohoto přepínače spustit doplněk z příkazového řádku. Další informace najdete v tématu [Postup: ovládání doplňků pomocí Správce doplňků](https://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Příklad
 Tento příklad spustí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a automaticky spustí makro otevřít oblíbené soubory.

```
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Viz také
 [Parametry příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) – [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
