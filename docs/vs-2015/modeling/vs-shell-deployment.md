---
title: Nasazení prostředí VS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659308"
---
# <a name="vs-shell-deployment"></a>Nasazení prostředí VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Izolované prostředí vám umožní určit, které funkce sady Visual Studio budete potřebovat k interakci s jazykem konkrétní domény a jak se má toto řešení zobrazit. Další informace o izolovaném prostředí sady Visual Studio najdete v tématu [přizpůsobení izolovaného prostředí](../extensibility/customizing-the-isolated-shell.md). Další informace o tom, jak přizpůsobit izolované prostředí, najdete v tématu [přizpůsobení izolovaného prostředí](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Nastavení prostředí sady Visual Studio jako cíle nasazení

1. V projektu **DslPackage** otevřete **source.extension.TT**.

2. V části `<SupportedProducts>` Vložit:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Nahraďte *MyIsolatedShell* názvem vašeho balíčku izolovaného prostředí.
