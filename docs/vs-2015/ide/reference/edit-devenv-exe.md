---
title: -Edit (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c81f59f2dadf535af4e9a76949a29fd1355c33f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657747"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře zadaný soubor v existující instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Syntaxe

```
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Arguments
 `file1` volitelné. Soubor, který se má otevřít v existující instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Pokud žádná instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] neexistuje, vytvoří se nová instance s zjednodušeným rozložením okna a v nové instanci se otevře `file1`.

 `file2` volitelné. Jeden nebo více dalších souborů, které mají být otevřeny v existující instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="remarks"></a>Poznámky
 Pokud není zadán žádný soubor a existuje existující instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], existující instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dostane fokus. Pokud není zadaný žádný soubor a neexistuje žádná existující instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vytvoří se nová instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se zjednodušeným rozložením oken.

 Pokud je existující instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v modálním stavu, například pokud je [dialogové okno Možnosti](../../ide/reference/options-dialog-box-visual-studio.md) otevřené, soubor se otevře v existující instanci, když [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ukončí modální stav.

## <a name="example"></a>Příklad
 Tento příklad otevře soubor `MyFile.cs` v existující instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nebo otevře soubor v nové instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], pokud ještě neexistuje.

```
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Viz také
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
