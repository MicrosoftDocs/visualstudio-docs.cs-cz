---
title: 'Postupy: vyloučení nebo zahrnutí funkce CShort z instrumentace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c6234db781925e8c0558513cb7e8bc608b5cfea
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814681"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Postupy: vyloučení nebo zahrnutí funkce CShort z instrumentace
Ve výchozím nastavení, nástroje pro profilování vyloučit *malé funkce* z instrumentace. Malé funkce jsou krátkých funkcí, které neprovádějte žádné volání funkcí. Kromě těchto funkcí malé poskytuje pro menší nároky na instrumentace a proto zlepšení instrumentace rychlost. Vyloučení malé funkcí také snižuje výkon profilace datový soubor (. *Vsp*) velikost a čas, který je vyžadován pro analýzu. Pokud malá funkce jsou vyloučeny, času stráveného v malých funkce započítává výhradní a včetně době jejich nadřazené funkce. Malé funkce můžete vyloučit nebo součástí instrumentace, jak je popsáno v následujícím postupu.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>K vyloučení nebo zahrnutí funkce CShort z instrumentace  
  
1.  V **prohlížeč výkonu**, vyberte **výkonnostní relace** a potom klikněte pravým tlačítkem a vyberte **vlastnosti**.  
  
     **Stránky vlastností** se zobrazí dialogové okno.  
  
2.  V **stránky vlastností**, klikněte **instrumentace** vlastnosti.  
  
3.  Vyloučení krátkých funkcí z instrumentace, vyberte **vyloučení krátkých funkcí z instrumentace**. Toto je výchozí nastavení.  
  
     -nebo-  
  
     Chcete-li zahrnout krátkých funkcí instrumentace, zrušte **vyloučení krátkých funkcí z instrumentace**.  
  
4.  Click **OK**.  
  
## <a name="see-also"></a>Viz také:  
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)   
 [Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)