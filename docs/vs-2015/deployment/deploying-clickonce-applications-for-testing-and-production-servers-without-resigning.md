---
title: Nasazování aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395375"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Nasazování aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje novou funkci ClickOnce představenou ve verzi .NET Framework 3,5, která umožňuje nasazení aplikací ClickOnce z více síťových umístění bez opětovného podepsání nebo změny manifestů ClickOnce.  
  
> [!NOTE]
> Opětovné podepisování je stále upřednostňovanou metodou pro nasazení nových verzí aplikací. Kdykoli je to možné, použijte metodu opětovného podepsání. Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Vývojáři třetích stran a prodejci softwaru se mohou k této funkci vyjádřit, což usnadňuje zákazníkům aktualizovat aplikace. Tato funkce se dá použít v následujících situacích:  
  
- Při aktualizaci aplikace, nikoli první instalace aplikace.  
  
- V případě, že je v počítači pouze jedna konfigurace aplikace. Pokud je například aplikace nakonfigurovaná tak, aby odkazovala na dvě různé databáze, nemůžete tuto funkci použít.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Vyloučení deploymentProvideru z manifestů nasazení  
 V .NET Framework 2,0 a .NET Framework 3,0 musí jakákoli aplikace ClickOnce, která je nainstalována v systému pro offline dostupnost, určovat `deploymentProvider` v manifestu nasazení. `deploymentProvider`Je často označován jako umístění aktualizace. Jedná se o umístění, ve kterém bude ClickOnce kontrolovat aktualizace aplikace. Tento požadavek, který je spojený s potřebou vydavatelů aplikací k podepisování jejich nasazení, je obtížné, aby společnost aktualizovala aplikaci ClickOnce od dodavatele nebo jiné třetí strany. Je také obtížné nasadit stejnou aplikaci z více míst ve stejné síti.  
  
 Se změnami, které byly provedeny v rámci ClickOnce v .NET Framework 3,5, je možné, že třetí strana poskytne aplikaci ClickOnce jiné organizaci, která pak může nasadit aplikaci do vlastní sítě.  
  
 Aby bylo možné tuto funkci využít, vývojáři aplikací ClickOnce musí `deploymentProvider` ze svých manifestů nasazení vyloučit. To znamená vyloučení `-providerUrl` argumentu při vytváření manifestů nasazení pomocí Mage.exe nebo zajistěte, aby textové pole **umístění spuštění** na kartě **manifest aplikace** bylo ponecháno prázdné, pokud generujete manifesty nasazení pomocí MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider a aktualizace aplikace  
 Počínaje verzí .NET Framework 3,5 již nemusíte v manifestu nasazení určovat, aby bylo `deploymentProvider` možné nasadit aplikaci ClickOnce pro použití v režimu online i offline. To podporuje scénář, ve kterém potřebujete zabalit a podepsat nasazení sami, ale umožněte jiným společnostem nasadit aplikaci přes jejich sítě.  
  
 Klíčovým bodem, který je třeba pamatovat, je, že aplikace, které vylučují, `deploymentProvider` nemohou měnit umístění instalace během aktualizací, dokud dostanou aktualizaci, která obsahuje `deploymentProvider` značku znovu.  
  
 Tady jsou dva příklady pro objasnění tohoto bodu. V prvním příkladu publikujete aplikaci ClickOnce, která nemá žádnou `deploymentProvider` značku, a požádáte uživatele, aby si ji instalovali `http://www.adatum.com/MyApplication/` . Pokud se rozhodnete, že chcete publikovat další aktualizaci aplikace z nástroje `http://subdomain.adatum.com/MyApplication/` , nebudete mít žádný způsob, jak to označit v manifestu nasazení, který se nachází v `http://www.adatum.com/MyApplication/` . Můžete provést jednu z následujících akcí:  
  
- Informujte uživatele o odinstalaci předchozí verze a nainstalujte novou verzi z nového umístění.  
  
- Zahrňte aktualizaci na `http://www.adatum.com/MyApplication/` , která obsahuje `deploymentProvider` ukazující na `http://www.adatum.com/MyApplication/` . Pak další aktualizaci uvolněte později pomocí `deploymentProvider` kurzoru na `http://subdomain.adatum.com/MyApplication/` .  
  
  V druhém příkladu publikujete aplikaci ClickOnce, která určuje `deploymentProvider` a následně se rozhodnete ji odebrat. Po stažení nové verze `deploymentProvider` do klientů nebude možné přesměrovat cestu použitou pro aktualizace, dokud nevyberete verzi vaší aplikace, která se `deploymentProvider` obnovila. Stejně jako u prvního příkladu `deploymentProvider` musí zpočátku nasměrovat na aktuální umístění aktualizace, nikoli na nové umístění. Pokud se v takovém případě pokusíte vložit `deploymentProvider` , který odkazuje na `http://subdomain.adatum.com/MyApplication/` , pak se další aktualizace nezdaří.  
  
## <a name="creating-a-deployment"></a>Vytvoření nasazení  
 Podrobné pokyny týkající se vytváření nasazení, která se dají nasadit z různých síťových umístění, najdete v tématu [Návod: Ruční nasazení aplikace ClickOnce, která nevyžaduje Opětovné podepsání a které zachovává informace o značkách](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
