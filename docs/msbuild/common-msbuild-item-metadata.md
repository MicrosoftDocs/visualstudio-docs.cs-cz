---
title: Společná metadata položky MSBuild | Microsoft Docs
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c715c16782733a08bb617a464c1aa9510d35b54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87425953"
---
# <a name="common-msbuild-item-metadata"></a>Společná metadata položky MSBuild

V následující tabulce jsou popsána volitelná metadata položek, která mají význam pro některé sady MSBuild SDK nebo cíle, ale které nejsou nastaveny ve výchozím nastavení pro každou položku. Můžete je nastavit tak, aby ovlivnily chování sestavení, ale pouze v případě, že je sada SDK nebo cílové soubory, které používáte, rozpoznána.

| Metadata položky | Sady SDK | Popis |
|---------------| ------- | -------------|
|% (Odkaz)| Vše |Systém projektu sady Visual Studio používá `Link` metadata (Pokud je k dispozici) pro změnu, co se zobrazí ve stromové struktuře projektu. soubor lze umístit do jiné struktury logické složky v **Průzkumník řešení**.<br />Kromě toho `AssignTargetPath` úkol vyhledá v `Link` poli Výstupní adresář, do kterého se má zkopírovat soubor, pokud se jedná o jednu z položek, které se zkopírovaly.|
|% (Propojení)| Sada .NET Core SDK | Slouží k nastavení složky, která se má použít pro `Link` metadata pro skupiny položek. |

## <a name="see-also"></a>Viz také

- [Obecné vlastnosti projektu nástroje MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
- [Metadata známé položky nástroje MSBuild](msbuild-well-known-item-metadata.md)