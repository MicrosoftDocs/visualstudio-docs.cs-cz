---
title: -Out (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 075746353440462a66133cd83ed9158470d8de5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662203"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje soubor pro ukládání a zobrazování chyb při spuštění, sestavení, opětovném sestavení nebo nasazení řešení.

## <a name="syntax"></a>Syntaxe

```
devenv /out FileName
```

## <a name="arguments"></a>Arguments
 `FileName` nutné. Cesta a název souboru, pro které se mají zobrazit chyby při vytváření spustitelného souboru.

## <a name="remarks"></a>Poznámky
 Pokud je zadán název souboru, který neexistuje, je soubor vytvořen automaticky. Pokud soubor již existuje, jsou výsledky připojeny k existujícímu obsahu souboru.

 Chyby sestavení příkazového řádku se zobrazí v **příkazovém** okně a v zobrazení tvůrce řešení v okně **výstup** . Tato možnost je užitečná, pokud spouštíte bezobslužné sestavení a potřebujete zobrazit výsledky.

## <a name="example"></a>Příklad
 V tomto příkladu se spustí `MySolution` a zapíše chyby do souboru `MyErrorLog.txt`.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Viz také
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv. exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)
