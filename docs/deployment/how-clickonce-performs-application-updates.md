---
title: Jak ClickOnce provádí aktualizaci aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1f5d9b67633ffa2b14f780b9588f526372a4f5d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152510"
---
# <a name="how-clickonce-performs-application-updates"></a>Jak ClickOnce provádí aktualizaci aplikací
Informace o verzi souboru, zadaný v manifestu nasazení aplikace ClickOnce využívající rozhodnout, jestli se má aktualizovat soubory aplikace. Po zahájení aktualizace ClickOnce pomocí techniky označované jako *soubor opravy* aby se zabránilo redundantní stahování souborů aplikace.  
  
## <a name="file-patching"></a>Oprava souborů  
 Při aktualizaci aplikace ClickOnce všechny soubory pro novou verzi aplikace nebude stahovat Pokud soubory se změnily. Místo toho porovná podpisy hodnoty hash souborů zadaných v manifestu aplikace pro aktuální aplikaci proti podpisy v manifestu pro novou verzi. Pokud se podpisy souboru liší, ClickOnce, soubory ke stažení na novou verzi. Pokud se podpisy shodují, soubor nebyl změněn z jedné verze na další. V tomto případě ClickOnce zkopíruje existující soubor a používá ho v nové verzi aplikace. Tento postup brání ClickOnce museli stáhnout celý aplikaci znovu spustit, i v případě, že pouze jeden nebo dva soubory se změnily.  
  
 Soubor opravy také funguje pro sestavení, které se stáhnou na vyžádání pomocí <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> a <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metody.  
  
 Pokud používáte sadu Visual Studio ke kompilaci vaší aplikace, vygeneruje se nové podpisy hodnoty hash pro všechny soubory pokaždé, když se je znovu sestavit celý projekt. V takovém případě všechna sestavení se stáhne do klienta, i když možná změnily pouze několik sestavení.  
  
 Oprava souborů pro soubory, které jsou označeny jako data a uloženy v adresáři dat nefunguje. Tyto budou staženy vždy bez ohledu na hodnoty hash podpisu souboru. Další informace o do adresáře dat, naleznete v tématu [přístup k lokálním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Viz také:  
 [Volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)