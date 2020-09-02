---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657910"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Upozorňuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] na sloučení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] balíčků v systému a Prohlédněte si všechny změny v mezipaměti MEF.

## <a name="syntax"></a>Syntax

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Poznámky
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spustí tento příkaz automaticky při instalaci balíčku VSIX. Měli byste spustit `devenv.exe /updateconfiguration` po opravě souborů tak, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se aktualizace mezipaměti MEF. To vám umožní vyhodnotit, jestli je vaše oprava adekvátní.

## <a name="example"></a>Příklad
 Následující příkazový řádek způsobí, že [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sloučí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] balíčky v systému a ZKONTROLUJE mezipaměť MEF pro všechny změny.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Viz také
 [Přizpůsobení nastavení vývoje v](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [přepínačích příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) sady Visual Studio
