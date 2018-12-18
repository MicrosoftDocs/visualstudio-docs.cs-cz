---
title: Nasazování aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 2b2a26e847a23e8a4037958532889626a931341c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840035"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Nasazování aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje nové funkce zavedena v rozhraní .NET Framework verze 3.5, která umožňuje nasazení aplikací ClickOnce z více umístění v síti bez opětovné podepsání nebo změna ClickOnce, manifesty ClickOnce.  
  
> [!NOTE]
>  Opětovné podepisování je stále upřednostňovanou metodou pro nasazení nové verze aplikací. Kdykoli je to možné, použijte metodu opětovného podepisování. Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Vývojáři třetích stran a nezávislé výrobce softwaru můžete vyjádřit výslovný souhlas s touto funkcí snadnější svým zákazníkům aktualizovat svoje aplikace. Tuto funkci můžete použít v následujících situacích:  
  
-   Při aktualizaci aplikace, ne první instalaci aplikace.  
  
-   Pokud existuje pouze jedna konfigurace aplikace na počítači. Například pokud aplikace je nakonfigurovaná tak, aby odkazoval na dvou různých databázích, nemůžete použít tuto funkci.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Vyloučení deploymentProvider z manifesty nasazení  
 V rozhraní .NET Framework 2.0 a rozhraní .NET Framework 3.0, musíte zadat jakékoli aplikace ClickOnce, která nainstaluje na systém pro dostupnost v režimu offline `deploymentProvider` v manifestu nasazení. `deploymentProvider` Se často označuje jako umístění aktualizace; je umístění, ve kterém ClickOnce vyhledá aktualizace aplikace. Tento požadavek spolu s potřebou vydavatelé aplikací k podepisování svých nasazení bylo obtížné zjišťovat společnosti k aktualizaci aplikace ClickOnce od dodavatele nebo jiných výrobců. Také umožňuje složitější nasazení stejnou aplikaci z více míst ve stejné síti.  
  
 Změny, které byly provedeny ClickOnce v rozhraní .NET Framework 3.5 je možné pro třetí strany k poskytování aplikace ClickOnce do jiné organizace, které pak můžete nasadit aplikaci na vlastní síť.  
  
 Aby bylo možné tuto funkci využít, musí vývojáři aplikací ClickOnce vyloučit `deploymentProvider` z jejich nasazení manifestů. To znamená, s výjimkou `-providerUrl` manifesty argument, když vytvoříte nasazení s Mage.exe nebo zajištěním, že **umístění spuštění** textového pole na **Manifest aplikace** karta je ponecháno prázdné Pokud jste manifesty nasazení s MageUI.exe jsou generovány.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider a aktualizace aplikací  
 Od verze rozhraní .NET Framework 3.5, nepotřebujete k určení `deploymentProvider` v manifestu nasazení k nasazení aplikace ClickOnce pro použití online i offline. Tento atribut podporuje scénář, kde je potřeba balíček a podepsat nasazení, ale povolit jinými společnostmi dohody o nasazení aplikace v jejich sítích.  
  
 Zásadním aspektem pamatovat je, že aplikace, které vyloučit `deploymentProvider` nelze změnit jejich umístění instalace během aktualizace, dokud nebude dodána aktualizace, která zahrnuje `deploymentProvider` označit znovu.  
  
 Tady jsou dva příklady pro objasnění tohoto bodu. V prvním příkladu, publikování aplikace ClickOnce, která nemá žádné `deploymentProvider` značku a zeptejte se uživatele k jeho nainstalování z http://www.adatum.com/MyApplication/. Pokud je rozhodnout, kterou chcete publikovat další aktualizace aplikací z http://subdomain.adatum.com/MyApplication/, nemůžete se nijak to zaznamenat v manifestu nasazení, který se nachází v http://www.adatum.com/MyApplication/. Jedním ze dvou kroků:  
  
- Řekněte uživatelům, aby odinstalovat předchozí verzi a nainstalujte novou verzi z nového umístění.  
  
- Zahrnout aktualizace na http://www.adatum.com/MyApplication/ , který obsahuje `deploymentProvider` odkazující na http://www.adatum.com/MyApplication/. Uvolněte později s jinou aktualizaci `deploymentProvider` odkazující na http://subdomain.adatum.com/MyApplication/.  
  
  V druhém příkladu publikování aplikace ClickOnce, která určuje `deploymentProvider`, a potom se rozhodnete ho odebrat. Jednou na novou verzi bez `deploymentProvider` byl stažen do klientů, nebude možné přesměrovat cestu používané pro aktualizace, dokud vydání verze aplikace, která má `deploymentProvider` obnovit. Stejně jako v prvním příkladu `deploymentProvider` zpočátku musí odkazovat na aktuální umístění aktualizace, nikoliv do nového umístění. V takovém případě pokud se pokusíte vložit `deploymentProvider` , který odkazuje na http://subdomain.adatum.com/MyApplication/, pak příští aktualizace se nezdaří.  
  
## <a name="creating-a-deployment"></a>Vytvoření nasazení  
 Podrobné pokyny k vytvoření nasazení, která se dají nasadit z různých síťových umístěních, najdete v části [návod: Ruční nasazení aplikace ClickOnce této nemá není vyžadují Re-Signing a zachová značky informací](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (generování manifestu a nástroj pro úpravy)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)



