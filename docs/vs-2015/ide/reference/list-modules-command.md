---
title: Listovat moduly – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4600f27f62d6e840041a65b4128df128e4d36873
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659532"
---
# <a name="list-modules-command"></a>Listovat moduly – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vypíše moduly pro aktuální proces.

## <a name="syntax"></a>Syntaxe

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametry
 /Address: `yes|no` volitelné. Určuje, zda se mají zobrazovat adresy paměti modulů. Výchozí hodnota je `yes` .

 /Name: `yes|no` volitelné. Určuje, zda se mají zobrazovat názvy modulů. Výchozí hodnota je `yes` .

 /Order: `yes|no` volitelné. Určuje, zda se má zobrazovat pořadí modulů. Výchozí hodnota je `no` .

 /Path: `yes|no` volitelné. Určuje, zda se mají zobrazovat cesty modulů. Výchozí hodnota je `yes` .

 /Process: `yes|no` volitelné. Určuje, zda se mají zobrazit procesy modulů. Výchozí hodnota je `no` .

 /SymbolFile: `yes|no` volitelné. Určuje, zda se mají zobrazovat soubory symbolů modulů. Výchozí hodnota je `no` .

 /SymbolStatus: `yes|no` volitelné. Určuje, zda se mají zobrazovat stavy symbolů modulů. Výchozí hodnota je `yes` .

 /Timestamp: `yes|no` volitelné. Určuje, zda se mají zobrazovat časová razítka modulů. Výchozí hodnota je `no` .

 /Version: `yes|no` volitelné. Určuje, zda se mají zobrazovat verze modulů. Výchozí hodnota je `no` .

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad
 V tomto příkladu jsou uvedeny názvy modulů, adresy a časová razítka pro aktuální proces.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Viz také
 [Příkazové okno](../../ide/reference/command-window.md) pro [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md) [: použití okna moduly](../../debugger/how-to-use-the-modules-window.md)
