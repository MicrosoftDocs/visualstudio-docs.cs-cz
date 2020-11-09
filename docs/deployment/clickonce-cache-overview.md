---
title: Přehled mezipaměti ClickOnce | Microsoft Docs
description: Seznamte se s mezipamětí aplikace ClickOnce, která obsahuje skryté adresáře na klientském počítači, kde jsou uloženy aplikace ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed4bc8d045ff21a536016edc0a0ac64d99c63c2f
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383102"
---
# <a name="clickonce-cache-overview"></a>Přehled mezipaměti ClickOnce
Všechny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, bez ohledu na to, jestli jsou místně nainstalované nebo hostované online, jsou uložené v klientském počítači v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *mezipaměti* aplikace. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Mezipaměť je řada skrytých adresářů v adresáři místní nastavení složky Dokumenty a nastavení aktuálního uživatele. Tato mezipaměť obsahuje všechny soubory aplikace, včetně sestavení, konfiguračních souborů, nastavení aplikace a uživatele a datového adresáře. Mezipaměť je také zodpovědná za migraci datového adresáře aplikace na nejnovější verzi. Další informace o migraci dat najdete v tématu [přístup k místním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 Poskytnutím jediného umístění pro úložiště aplikací [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] převezme úloha správy fyzické instalace aplikace od uživatele. Mezipaměť také pomáhá izolovat aplikace uchováváním sestavení a datových souborů pro všechny aplikace a jejich různých verzí odděleně od sebe. Například při upgradu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace je tato verze a její datové prostředky dodávány s vlastními adresáři v mezipaměti.

## <a name="cache-storage-quota"></a>Kvóta úložiště mezipaměti
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, které jsou hostované online, jsou omezené v množství místa, které můžou zabírat kvótou, která omezuje velikost [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mezipaměti. Velikost mezipaměti se vztahuje na všechny online aplikace uživatele. jediná částečně důvěryhodná, online aplikace je omezená na využívání poloviny prostoru kvót. Nainstalované aplikace nejsou omezeny velikostí mezipaměti a nepočítají se s limitem mezipaměti. V případě všech [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací uchovává mezipaměť pouze aktuální verzi a dříve nainstalovanou verzi.

 Ve výchozím nastavení mají klientské počítače 250 MB úložiště pro online [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. Datové soubory se nepočítají do tohoto limitu. Správce systému může tuto kvótu na konkrétním klientském počítači zvětšit nebo zmenšit změnou klíče registru **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB** , což je hodnota DWORD, která vyjadřuje velikost mezipaměti v kilobajtech. Chcete-li například zmenšit velikost mezipaměti na 50 MB, změňte tuto hodnotu na 51200.

## <a name="see-also"></a>Viz také
- [Přístup k místním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)