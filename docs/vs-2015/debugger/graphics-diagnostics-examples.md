---
title: Příklady diagnostiky grafiky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9c4a5f3396992b8bca2756b33b9b6f920d54733
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776119"
---
# <a name="graphics-diagnostics-examples"></a>Příklady diagnostiky grafiky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto příklady ukazují, jak k ladění problémů s vykreslováním v aplikacích založených na rozhraní DirectX pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostiky grafiky.  
  
## <a name="capturing-graphics-information"></a>Zachycení informací grafiky  
 Před diagnostiky grafiky můžete použít k diagnostice problémů s vykreslováním v aplikaci, budete muset zachytit informace grafiky z aplikace během jejího běhu. Dají zachytit informace grafiky z aplikace, na kterém běží místně, nebo z aplikace, na kterém běží na vzdáleném počítači nebo jiném zařízení. Tyto postupy ukazují, jak můžete zachytit informace grafiky z aplikace ručně nebo prostřednictvím kódu programu:  
  
-   [Návod: Zaznamenání grafických informací](../debugger/walkthrough-capturing-graphics-information.md)  
  
-   [Návod: Zaznamenání grafických informací prostřednictvím kódu programu](../debugger/walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Použití diagnostiky grafiky se zařízením založené na ARM  
 Diagnostika grafiky můžete použít k ladění aplikace rozhraní Direct3D zařízení založené na ARM pomocí vzdáleného ladění. Další informace najdete v části [postupy: použití diagnostiky grafiky se zařízením ARM](../debugger/how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Přehrávání grafické informace  
 Poté, co můžete zachytit informace grafiky z běžící aplikaci, můžete přehrávat zachycené události k diagnostice problémů vykreslování. Chcete-li přehrát, můžete používat svůj vývojářský počítač nebo můžete použít vzdálený počítač nebo zařízení, které jsou připojené k. Další informace najdete v tématu [postupy: Změna počítače pro přehrávání diagnostiky grafiky](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Ladění chybějící objekty  
 Chybí objekt (nebo objekty) je jedním z nejběžnějších problémů s vykreslováním, které vývojáři grafické prostředí. Tento druh problému může být obtížné diagnostikovat, protože různé druhy chyb může způsobit, že objekt zjevně zmizí. Obvyklým případem chybějících objekty patří nesprávné konfigurace stavu. problémy při transformaci geometrie objektu nebo nesprávně nakonfigurované grafickém kanálu.  
  
 Tyto scénáře ukazují použití diagnostiky grafiky a zjistit, proč je objekt chybí kód, který je zodpovědný.  
  
-   [Návod: Chybějící objekty z důvodu stavu zařízení](../debugger/walkthrough-missing-objects-due-to-device-state.md)  
  
-   [Návod: Chybějící objekty z důvodu použití funkce vertex shading](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)  
  
-   [Návod: Chybějící objekty z důvodu nesprávné konfigurace zřetězení](../debugger/walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>Ladění chyb při vykreslování  
 Objekt (nebo objekty) nemají správné vzhled je jiný běžný problém, který vývojářům grafické prostředí. Tento druh problému může být obtížné diagnostikovat, protože nesprávný vzhled a jeho příčinu, může být v rozsahu od velmi zřejmé – vazby nesprávné textury – velmi malé – chyby v kódu shaderu nebo neočekávané interakce mezi shadery. Některé problémy mohou způsobovat kombinaci chyb.  
  
 Tady je scénář, který ukazuje použití diagnostiky grafiky k vysledování není tak drobným vykreslování problém, který způsobuje chybu menší shaderu:  
  
-   [Návod: Ladění chyb při vykreslování způsobených stínováním](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>Ladění výpočetních shaderů  
 Diagnostika grafiky můžete použít k ladění jádra výpočetního shaderu DirectCompute, které generují nesprávné výsledky. S DirectCompute slouží k provádění výpočtů na velký počet datových elementů paralelně výpočetní výkon GPU. Pro některé druhy problémů, využití GPU můžete provést tolikrát, kolikrát rychleji než i dobře optimalizovaný kód procesoru. Tradiční ladicí programy však nelze zjistit kód, který běží na GPU. Tento druh kódu ladění vyžaduje specializované nástroje, které jsou často specifického pro dodavatele a nemusí se integrují s Visual Studio. Chcete-li ladění výpočetního shaderu konzistentnější v rozsahu GPU, diagnostiky grafiky jsou zaznamenané události DirectCompute odeslání – kromě události vykreslování Direct3D – tak, že můžete používat známé nástroje pro ladění problémů v kódu výpočetního shaderu.  
  
 Scénář, který ukazuje, jak ladit simulace problém způsobený chybou v výpočetního shaderu, najdete v článku [návod: použití diagnostiky grafiky, chcete-li ladit výpočetní Shader](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).



