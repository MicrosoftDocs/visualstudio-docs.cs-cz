---
title: Příklady diagnostiky grafiky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6816cced178e6e76a8fe33e37bbb075d1318c999
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474301"
---
# <a name="graphics-diagnostics-examples"></a>Příklady diagnostiky grafiky
Tyto příklady ukazují, jak ladit vykreslování problémy s aplikací založených na rozhraní DirectX pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostiky grafiky.  
  
## <a name="capturing-graphics-information"></a>Zachycení informací grafiky  
 Před použitím diagnostiky grafiky k diagnostikování problémů vykreslování ve vaší aplikaci, budete muset zaznamenání grafických informací z aplikace, když je spuštěná. Grafických informací se dají zachytit z aplikace, která je spuštěna místně nebo aplikaci, která běží na vzdáleném počítači nebo jiné zařízení. Tyto postupy ukazují, jak zaznamenání grafických informací z aplikace ručně nebo z programu:  
  
-   [Návod: Zaznamenání grafických informací](walkthrough-capturing-graphics-information.md)  
  
-   [Návod: Zaznamenání grafických informací prostřednictvím kódu programu](walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Pomocí diagnostiky grafiky zařízení založené na ARM  
 Můžete diagnostiky grafiky k ladění aplikace Direct3D – na bázi ARM zařízení pomocí vzdáleného ladění. Další informace najdete v části [postupy: použití diagnostiky grafiky s ARM zařízením](how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Přehrávání grafických informací  
 Po zaznamenání grafických informací z spuštěné aplikaci, můžete přehrávat zaznamenané události, k diagnostikování problémů vykreslování. Přehrát, můžete použít vývojovém počítači, nebo můžete použít vzdálený počítač nebo zařízení, které jste připojeni k. Další informace najdete v tématu [postupy: Změna počítače pro přehrávání diagnostiky grafiky](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Ladění chybějící objekty  
 Objekt chybí (nebo objekty) je jedním nejběžnějších problémů vykreslování, které vývojáři grafické prostředí. Tento druh problému může být obtížné diagnostikovat, protože několik různých druhů chyb může způsobit, že objekt tak, aby zjevně zmizí. Typické pro chybějící objekty příčiny stavu nesprávně nakonfigurované zařízení, problémy v transformace geometrie objektu nebo nesprávně nakonfigurované grafiky kanálu.  
  
 Tyto scénáře ukazují, jak můžete diagnostiky grafiky a zjistit, proč je objekt chybějících kód, který je zodpovědný.  
  
-   [Návod: Chybějící objekty z důvodu stavu zařízení](walkthrough-missing-objects-due-to-device-state.md)  
  
-   [Návod: Chybějící objekty z důvodu použití funkce vertex shading](walkthrough-missing-objects-due-to-vertex-shading.md)  
  
-   [Návod: Chybějící objekty z důvodu nesprávné konfigurace zřetězení](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>Ladění chyb při vykreslování  
 Objekt (nebo objekty) nemá správný vzhled je jiného běžné problému, který vývojářům grafické prostředí. Tento druh problému může být obtížné diagnostikovat, protože nesprávný vzhled a jeho příčinu, může být v rozsahu od velmi zřejmé – vazby nesprávný texture – velmi malé – chybou v kódu shaderu nebo neočekávané interakcí mezi shadery. Některé problémy, může být způsobeno kombinaci chyb.  
  
 Tady je scénáře, který ukazuje použití diagnostiky grafiky k sledovat není tak jemně vykreslování problém způsobený menší shaderu chyb:  
  
-   [Návod: Ladění chyb při vykreslování způsobených stínováním](walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>Ladění výpočetní shadery  
 Můžete diagnostiky grafiky k ladění výpočetního shaderu jádra DirectCompute, které generují nesprávné výsledky. S DirectCompute můžete výpočetní výkon GPU provádět výpočty na velký počet datových elementů paralelně. Pro některé druhy problémů, využití GPU můžete provést mnohokrát rychleji než i dobře optimalizovaný kód procesoru. Tradiční ladicí programy však nelze rozpoznat kód, který běží na GPU. Ladění tento druh kódu vyžaduje specializované nástroje, které jsou často specifické pro dodavatele a nemusí integrovat s Visual Studio. Chcete-li výpočetního shaderu – ladění více konzistentní napříč rozsahu z grafickými procesory, diagnostiky grafiky jsou zaznamenané události, odesílání DirectCompute – kromě události vykreslování Direct3D – tak, aby známých nástrojů můžete použít pro ladění problémů ve vašem kódu výpočetního shaderu.  
  
 Scénář, který ukazuje, jak ladit simulace problém způsobený chybou v výpočetního shaderu najdete v tématu [návod: použití diagnostiky grafiky k ladění shaderu výpočetní](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).