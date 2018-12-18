---
title: ClickOnce – Přehled mezipaměti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d846ec60f6cf1722584c4ea93c56c29bc7007b89
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077617"
---
# <a name="clickonce-cache-overview"></a>ClickOnce – Přehled mezipaměti
Všechny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací, ať už jsou nainstalované místně nebo online, se ukládají v klientském počítači v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikace *mezipaměti*. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mezipaměť je řada skrytých složek v místní nastavení adresáři Documents and Settings složky aktuálního uživatele. Tato mezipaměť obsahuje soubory všechny aplikace, včetně sestavení, konfigurační soubory, aplikace a uživatelských nastavení a data adresáře. Mezipaměť je také zodpovědnost za migraci dat adresáře aplikace na nejnovější verzi. Další informace o migraci dat najdete v tématu [Accessing Local and Remote Data in ClickOnce Applications](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Tím, že poskytuje jedno umístění pro uložení aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] převezme úlohy správy fyzické instalace aplikace od uživatele. Mezipaměť také pomáhá izolovat aplikace podle sestavení a datové soubory pro všechny aplikace a jejich různé verze oddělit od sebe. Například při upgradu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, že verze a její datové prostředky se dodávají s jejich vlastní adresáře v mezipaměti.  
  
## <a name="cache-storage-quota"></a>Kvóta úložiště mezipaměti  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, které jsou hostované online jsou omezené množství místa, které mohou zabírat kvótou, která omezuje velikost [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mezipaměti. Velikost mezipaměti se vztahuje na všechny uživatele online aplikace; jednu aplikaci částečně důvěryhodné, online je omezena na polovinu kvóta místa. Nainstalované aplikace nejsou omezeny velikost mezipaměti a nezapočítávají limit mezipaměti. Pro všechny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací, mezipaměti zachová jenom aktuální verzi a dříve nainstalované verzi.  
  
 Ve výchozím nastavení, klientské počítače mají 250 MB úložiště pro online [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací. Datové soubory se nepočítají do tohoto limitu. Správce systému může zvětšit nebo zmenšit tato kvóta na konkrétní klientský počítač změnou klíče registru **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB**, což je hodnota DWORD, aby vyjadřoval velikost mezipaměti v kilobajtech. Například by za účelem snížení velikosti mezipaměti na 50 MB, změňte tuto hodnotu na 51200.  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k lokálním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)