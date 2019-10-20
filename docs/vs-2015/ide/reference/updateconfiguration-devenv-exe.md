---
title: -Updateconfiguration (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657910"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv. exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Oznamuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ke sloučení balíčků [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v systému a kontrolu mezipaměti MEF pro všechny změny.

## <a name="syntax"></a>Syntaxe

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Poznámky
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spustí tento příkaz automaticky při instalaci balíčku VSIX. Po opravování souborů byste měli spustit `devenv.exe /updateconfiguration`, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aktualizovat mezipaměť MEF. To vám umožní vyhodnotit, jestli je vaše oprava adekvátní.

## <a name="example"></a>Příklad
 Následující příkazový řádek způsobí, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sloučit balíčky [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v systému a ověřit mezipaměť MEF pro všechny změny.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Viz také
 [Přizpůsobení nastavení vývoje v](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [přepínačích příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) sady Visual Studio
