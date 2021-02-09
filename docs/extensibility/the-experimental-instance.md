---
title: Experimentální instance | Microsoft Docs
description: Přečtěte si, jak sada Visual Studio SDK poskytuje experimentální prostor pro spouštění netestovaných aplikací v režimu ladění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 728913596ce8c3947756906dffb144eecd3d71ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895268"
---
# <a name="the-experimental-instance"></a>Experimentální instance
Chcete-li chránit vývojové prostředí sady Visual Studio před netestovanými aplikacemi, které by ho mohly změnit, VSSDK poskytuje experimentální prostor, který můžete použít k experimentování. Nové aplikace vyvíjíte pomocí sady Visual Studio obvyklým způsobem, ale spouštíte je pomocí této experimentální instance.

 Každá aplikace, která má VSIX balíček, spustí experimentální instanci sady Visual Studio v režimu ladění.

 Pokud chcete spustit experimentální instanci sady Visual Studio mimo konkrétní řešení, spusťte následující příkaz v příkazovém okně:

 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe"/rootsuffix exp

> [!NOTE]
> Experimentální instance je zapsána do registru v `<version number>Exp` `<version number>Exp_Config` uzlech a. Například oblast experimentálního registru sady Visual Studio 2015 je
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` a `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Doporučujeme, abyste při vývoji tohoto rozšíření spustili v experimentální instanci. Když rozšíření nasadíte, spustí se v instanci vývoje. Další informace o registraci aplikací najdete v tématu [Registrace VSPackage](../extensibility/internals/registering-vspackages.md).
