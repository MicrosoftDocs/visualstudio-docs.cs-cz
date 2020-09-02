---
title: 'Postupy: automatické použití kódů Product Key při nasazení sady Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ec050cf8f365bfae2290593a0c7f215dcb2f39cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185996"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Postup: automatické použití kódů Product Key při nasazení sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [automatické použití kódů Product Key při nasazení sady Visual Studio](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

Kód Product Key můžete použít programově jako součást skriptu používaného k automatizaci nasazení sady Visual Studio 2015. Kódy Product Key lze v zařízení programově nastavit během instalace sady Visual Studio nebo po dokončení instalace.

## <a name="apply-the-license-during-installation"></a>Použití licence při instalaci
 Použijte parametr/ProductKey k použití kódu Product Key během procesu instalace sady Visual Studio. Tento parametr instalace lze použít s parametrem/Silent k instalaci sady Visual Studio do již licencovaného stavu pro koncového uživatele. Pokud chcete použít parametr/ProductKey, otevřete příkazový řádek. Spusťte instalační program (například vs_enterprise.exe nebo vs_professional.exe) a nastavte parametr/ProductKey s použitím kódu Product Key (25 znaků), který neobsahuje žádné pomlčky:

 Toto je příklad příkazu pro instalaci sady Visual Studio 2015 Enterprise s produktem Product Key AAAAABBBBBCCCCCDDDDDEEEEEEE:

 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`

## <a name="apply-the-license-after-installation"></a>Použití licence po instalaci
 Nainstalovanou verzi sady Visual Studio můžete aktivovat s použitím kódu Product Key pomocí nástroje storePID.exe v cílových počítačích v tichém režimu. StorePID.exe je program, který se instaluje se sadou Visual Studio v umístění ** \<drive> : \\ \Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**.

 Spusťte storePID.exe se zvýšenými oprávněními, a to buď pomocí agenta nástroje System Center, nebo příkazového řádku se zvýšenými oprávněními následovaných kódem Product Key (včetně pomlček) a kódu produktu společnosti Microsoft (MPC). Nezapomeňte do kódu Product Key přidat pomlčky.

 `StorePID.exe [product key including the dashes] [MPC]`

 Toto je příklad příkazového řádku pro instalaci sady Visual Studio 2015 Enterprise, která má MPC 07060, s klíčem Product Key "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE":

 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`

 V následující tabulce jsou uvedeny kódy MPC pro jednotlivé edice sady Visual Studio:

|Edice sady Visual Studio|MPC|
|---------------------------|---------|
|Visual Studio Enterprise 2015|07060|
|Visual Studio Professional 2015|07062|
|Visual Studio Test Professional 2015|07066|
|Visual Studio Ultimate 2013|06181|
|Visual Studio Premium 2013|06191|
|Visual Studio Professional 2013|06177|
|Visual Studio Test Professional 2013|06194|

Další informace o tom, jak získat kód Product Key, najdete v tématu [Postup: vyhledání kódu Product Key sady Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).

Pokud StorePID.exe úspěšně použili kód Product Key, vrátí hodnotu 0. Pokud dojde k chybám, vrátí se číslo od 1 do 6.

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio](../install/install-visual-studio-2015.md)