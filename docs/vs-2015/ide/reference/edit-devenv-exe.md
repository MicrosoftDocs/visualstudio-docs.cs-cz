---
title: -Edit (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657747"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře zadaný soubor v existující instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="syntax"></a>Syntaxe

```
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Argumenty
 `file1` Volitelné. Soubor, který se má otevřít v existující instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Pokud žádná instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] neexistuje, vytvoří se nová instance s zjednodušeným rozložením okna a otevře se `file1` v nové instanci.

 `file2` Volitelné. Jeden nebo více dalších souborů, které mají být otevřeny v existující instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="remarks"></a>Poznámky
 Pokud není zadán žádný soubor a existuje instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , existující instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dostane fokus. Pokud není zadaný žádný soubor a neexistuje žádná existující instance, vytvoří se [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Nová instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] s zjednodušeným rozložením okna.

 Pokud je existující instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v modálním stavu, například v případě, že je [dialogové okno Možnosti](../../ide/reference/options-dialog-box-visual-studio.md) otevřené, soubor se otevře v existující instanci, když dojde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] k ukončení modálního stavu.

## <a name="example"></a>Příklad
 Tento příklad otevře soubor `MyFile.cs` v existující instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nebo otevře soubor v nové instanci, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Pokud ještě neexistuje.

```
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Viz také
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
