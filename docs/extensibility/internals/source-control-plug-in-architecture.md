---
title: Zdrojová architektura modulu Plug-in Řízení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 498f3aeb87855a0dac5afacc1baa7e2e816375f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132388"
---
# <a name="source-control-plug-in-architecture"></a>Modul Plug-in architektury zdroje
Můžete přidat podporu zdroj ovládacího prvku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE) pomocí implementace a připojení modulu plug-in Správa zdrojového kódu. Prostředí IDE se připojí k modulu plug-in přes dobře definované API Plug-In zdroj řízení zdrojového kódu. Prostředí IDE zpřístupní funkcí správy zdrojového kódu pro řízení verze tím, že poskytuje uživatelské rozhraní (UI), která se skládá z panely nástrojů a příkazy nabídky. Modul plug-in správy zdroje implementuje funkce správy zdrojů.  
  
## <a name="source-control-plug-in-resources"></a>Modul Plug-in prostředky zdroj ovládacího prvku  
 Modul Plug-in Zdroj ovládacího prvku obsahuje materiály, které vám pomůžou vytvořit a správa verzí aplikaci připojit ke [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Modul Plug-in zdroj ovládací prvek obsahuje specifikaci rozhraní API, která musí být implementována zdrojového kódu, který je modul plug-in, takže může být integrovaná do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Obsahuje taky (napsané v jazyce C++) ukázka kódu, který implementuje na kostru zdroj ovládacího prvku modulu plug-in představujících implementace základních funkcí, které jsou kompatibilní s rozhraním API Plug-in Zdroj ovládacího prvku.  
  
 Specifikace rozhraní API modulu Plugin zdroj ovládacího prvku umožňuje využívat žádné systému správy zdrojů podle svého výběru, pokud vytvoříte ovládací prvek zdroje knihovny DLL s požadovanou sadu funkcí, které jsou implementované v souladu s rozhraní API ovládacího prvku Plug-in zdroje.  
  
## <a name="components"></a>Součásti  
 Zdrojový balíček adaptér ovládacího prvku v diagramu je součástí prostředí IDE, který překládá uživatele žádost o operaci správy zdrojů do volání funkce podporuje modul plug-in zdrojového kódu. K tomu dojít rozhraní IDE a Správa zdrojového kódu modul plug-in musí mít efektivní dialogu, který předává informace přepínat mezi IDE a modul plug-in. Pro toto dialogové okno proběhla obě musí kontaktovat ve stejném jazyce. Rozhraní API modulu Plugin zdroj ovládacího prvku uvedených v této dokumentaci je běžných termínů pro tento server exchange.  
  
 ![Zdroj Diagram architektury správy kódu](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
Diagram architektury znázorňující modulu plug-in interakce mezi VS a Správa zdrojového kódu  
  
 Jak je znázorněno v diagram architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí, které jsou označené jako VS prostředí v diagramu hostitelem pracovní projekty a související součásti, například editory a Průzkumník řešení uživatele. Zdrojový balíček ovládací adaptéru zpracovává interakci mezi IDE a modul plug-in zdrojového kódu. Zdrojový balíček ovládací adaptéru poskytuje vlastní zdrojového kódu uživatelského rozhraní. Je rozhraní nejvyšší úrovně, které uživatel komunikuje za účelem zahájení a definuje rozsah operaci správy zdrojů.  
  
 Správa zdrojového kódu modul plug-in může mít svůj vlastní uživatelské rozhraní, která se může skládat ze dvou částí, jak je znázorněno na obrázku. Pole s popiskem "Dodavatele uživatelského rozhraní" reprezentuje elementy vlastního uživatelského rozhraní, které, jako ovládací prvek zdroj modulu plug-in tvůrci, zadáte. Tyto se zobrazují přímo z modulu plug-in zdrojového kódu, když uživatel vyvolá operace pokročilé zdroj ovládacího prvku. Pole s popiskem "Pomocné rutiny uživatelského rozhraní" je sada zdroj ovládacího prvku modulu plug-in uživatelského rozhraní funkce, které jsou vyvolány nepřímo prostřednictvím rozhraní IDE. Modul plug-in správy zdroje předává zprávy týkající se uživatelského rozhraní IDE prostřednictvím speciální zpětného volání funkce poskytované rozhraní IDE. Pomocné rutiny uživatelského rozhraní usnadňuje více bezproblémovou integraci s rozhraní IDE (často prostřednictvím použitím z **Upřesnit** tlačítko) a tak poskytuje více jednotná činnost koncového uživatele.  
  
 Správa zdrojového kódu modulu plug-in nelze provádět změny k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí shell a v důsledku toho zdrojový balíček ovládací adaptéru nebo zdroj řídit uživatelského rozhraní, poskytuje rozhraní IDE. Ho musíte nastavit maximální využití flexibilitu nabízeným přes provádění různých funkcí rozhraní API modulu Plugin zdroj ovládacího prvku které přispívají k integrované možnosti pro koncového uživatele. Části referenční dokumentaci rozhraní API modulu Plugin řízení zdroj obsahuje informace pro modul plug-in funkcí některé pokročilé zdroj řízení. Modul plug-in správy zdroje zneužít tyto funkce, musí deklarovat jeho rozšířené možnosti IDE během inicializace a musí implementovat určité pokročilé funkce pro každou funkci.  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in programu zdroj ovládacího prvku](../../extensibility/source-control-plug-ins.md)   
 [Glosář](../../extensibility/source-control-plug-in-glossary.md)   
 [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)