---
title: Experimentální instance | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699030"
---
# <a name="the-experimental-instance"></a>Experimentální instance
Chcete-li chránit vývojové prostředí sady Visual Studio před netestovanými aplikacemi, které by jej mohly změnit, poskytuje sada VSSDK experimentální prostor, který můžete použít k experimentování. Vyvíjíte nové aplikace pomocí sady Visual Studio jako obvykle, ale spustit je pomocí této instance experimentální.

 Každá aplikace, která má balíček VSIX spustí visual studio experimentální instance v režimu ladění.

 Pokud chcete spustit experimentální instanci sady Visual Studio mimo konkrétní řešení, spusťte v příkazovém okně následující příkaz:

 "*\<Cesta k instalaci sady Visual studio>* \Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> Experimentální instance je zapsána do `<version number>Exp` `<version number>Exp_Config` registru pod uzly a. Například oblast experimentálního registru sady Visual Studio 2015 je
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` a `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Doporučujeme spustit rozšíření v experimentální instanci při jeho vývoji. Při nasazení rozšíření se spustí v instanci vývoje. Další informace o registraci aplikací naleznete v [tématu Registrace balíčků VSPackages](../extensibility/internals/registering-vspackages.md).
