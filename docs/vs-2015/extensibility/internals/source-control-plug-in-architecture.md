---
title: Architektura modulu Plug-in správy zdrojového | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7ded33f6296d9ddb0b87a3d2916a95249169f82
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805206"
---
# <a name="source-control-plug-in-architecture"></a>Architektura modulu plug-in správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Můžete přidat podporu zdrojového ovládacího prvku [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) pomocí implementace a připojení modulu plug-in správy zdrojového kódu. Rozhraní IDE se připojí k prostřednictvím dobře definovaných rozhraní API modulu Plug-In ovládací prvek zdroj modulu plug-in správy zdrojového kódu. Rozhraní IDE poskytuje funkce správy zdrojového kódu pro řízení verze tím, že poskytuje uživatelské rozhraní (UI), který se skládá z panelů nástrojů a příkazů nabídky. Modul plug-in správy zdrojového kódu implementuje funkce správy zdrojového kódu.  
  
## <a name="source-control-plug-in-resources"></a>Modul Plug-in zdroje ovládacího prvku zdroje  
 Modul Plug-in zdroje ovládacího prvku poskytuje prostředky umožňující vytvoření a připojení správy verzí aplikace [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Obsahuje specifikace rozhraní API, která se musí implementovat modul plug-in správy zdrojového kódu tak, aby ho bylo možné integrovat do modulu Plug-in zdroje ovládacího prvku [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Obsahuje taky ukázku kódu (napsaného v jazyce C++), který implementuje na kostru zdrojový ovládací prvek modulu plug-in představujících implementace základní funkce, které jsou kompatibilní s rozhraním API modulů Plug-in zdroje ovládacího prvku.  
  
 Specifikace rozhraní API modulu Plug-in zdroje ovládacího prvku umožňuje využívat všechny systému správy zdrojového kódu podle vašeho výběru, vytváření knihovny DLL správy zdrojového kódu s požadovanou sadu funkcí, které jsou implementovány v souladu s rozhraní API modulu Plug-in zdroje ovládacího prvku.  
  
## <a name="components"></a>Součásti  
 Zdrojový balíček adaptér ovládacího prvku v diagramu je součástí integrovaného vývojového prostředí, který překládá uživatelského požadavku pro operaci správy zdrojových kódů do volání funkce podporuje modul plug-in správy zdrojového kódu. K tomu dojde rozhraní IDE a modulu plug-in správy zdrojového kódu musí mít platné dialogového okna, který předává informace vpřed a zpět mezi integrovaného vývojového prostředí a modulu plug-in. Pro toto dialogové okno uskutečnit musí oba mluvit stejný jazyk. Rozhraní API modulu Plug-in zdroje ovládacího prvku uvedených v této dokumentaci je běžné slovník pro tuto výměnu.  
  
 ![Zdrojový kód Diagram architektury správy](../../extensibility/internals/media/vs-sccsdk-plug-in-arch.gif "vs_sccsdk_plug_in_arch")  
Diagram architektury znázorňující interakce mezi VS a Správa zdrojového kódu modulu plug-in  
  
 Jak je znázorněno v diagramu architektury [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí, které jsou označeny jako prostředí VS v diagramu je hostitelem přidružené komponenty, například editory a Průzkumník řešení a pracovní projekty uživatele. Zdrojový ovládací prvek adaptér balíček zpracovává interakce mezi integrovaného vývojového prostředí a modulu plug-in správy zdrojového kódu. Zdrojový ovládací prvek adaptér balíček poskytuje vlastní zdrojový ovládací prvek uživatelského rozhraní. Je nejvyšší úrovně uživatelského rozhraní, které uživatel pracuje se, aby bylo možné zahájit a definuje rozsah operaci správy zdrojových kódů.  
  
 Modul plug-in správy zdrojového kódu může mít svůj vlastní uživatelské rozhraní, která se může skládat ze dvou částí, jak je znázorněno na obrázku. Pole s názvem "Dodavatel uživatelského rozhraní" představuje vlastních prvků uživatelského rozhraní, které, jako ovládací prvek modulu plug-in autora zdroj, zadáte. Když uživatel vyvolá operaci pokročilé zdrojového ovládacího prvku se zobrazí přímo pomocí modulu plug-in správy zdrojového kódu. Pole s popiskem "Uživatelské rozhraní pomocné rutiny" je sada funkcí správy zdrojového kódu modulu plug-in uživatelského rozhraní, které jsou nepřímo vyvolané prostřednictvím integrovaného vývojového prostředí. Modul plug-in správy zdrojového kódu předává zprávy související s Uživatelským prostředím IDE prostřednictvím speciální zpětného volání funkce poskytované rozhraní IDE. Pomocné rutiny uživatelského rozhraní zajišťuje bezproblémové integraci s integrovaného vývojového prostředí (často prostřednictvím použití aplikace **Upřesnit** tlačítko) a poskytne tak více jednotné prostředí koncového uživatele.  
  
 Modul plug-in správy zdrojového kódu nemůže provést změny [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí a v důsledku toho balíček adaptéru ovládací prvek zdroje nebo zdroje ovládací prvek uživatelského rozhraní poskytované rozhraní IDE. Maximální využití flexibilitě, kterou nabízí prostřednictvím implementace různých funkcí rozhraní API modulu Plug-in zdroje ovládacího prvku, které přispívají k integrované prostředí pro koncové uživatele musí vytvořit. Informační části dokumentace k rozhraní API modulu Plug-in zdroje ovládacího prvku obsahuje informace o některé pokročilé zdroj modulu plug-in funkce ovládacího prvku. Zneužít tyto funkce, modul plug-in správy zdrojového kódu musí deklarovat své pokročilé funkce rozhraní IDE při inicializaci a musí implementovat konkrétní pokročilé funkce pro každou funkci.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek moduly plug-in zdrojového kódu](../../extensibility/source-control-plug-ins.md)   
 [Glosář](../../extensibility/source-control-plug-in-glossary.md)   
 [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)

