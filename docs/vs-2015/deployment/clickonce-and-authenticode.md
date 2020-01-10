---
title: ClickOnce a Authenticode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e48039a618f7e8eef7f2c6e9f097da87e37d0f5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847787"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce a kód Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode * je technologie Microsoftu, která používá standardní kryptografii k podepsání kódu aplikace digitálními certifikáty, které ověřují pravost vydavatele aplikace. Pomocí technologie Authenticode pro nasazení aplikací [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] snižuje riziko trojského koně. Trojský kůň je Vir nebo jiný škodlivý program, který škodlivá třetí strana nepředstavuje legitimní program pocházející z vytvořeného důvěryhodného zdroje. Podepisování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení pomocí digitálního certifikátu je volitelný krok k ověření, že sestavení a soubory nejsou úmyslně poškozeny.  
  
 Následující části popisují různé typy digitálních certifikátů používaných v technologii Authenticode, způsob ověřování certifikátů pomocí certifikačních autorit (CA), role časového razítka v certifikátech a metody úložiště dostupné pro certifikáty.  
  
## <a name="authenticode-and-code-signing"></a>Technologie Authenticode a podepisování kódu  
 *Digitální certifikát* je soubor, který obsahuje kryptografický pár veřejného a privátního klíče, spolu s metadaty, které popisují vydavatele, kterým byl certifikát vystavený, a agenturou, která certifikát vystavila.  
  
 Existují různé typy certifikátů technologie Authenticode. Každá z nich je nakonfigurována pro různé typy podepisování. Pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace musíte mít certifikát Authenticode, který je platný pro podepisování kódu. Pokud se pokusíte podepsat aplikaci [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] s jiným typem certifikátu, například digitálním e-mailovým certifikátem, nebude to fungovat. Další informace najdete v tématu [Úvod do podepisování kódu](https://msdn.microsoft.com/library/ms537361.aspx).  
  
 Certifikát pro podepsání kódu můžete získat jedním ze tří způsobů:  
  
- Zakupte si ho od dodavatele certifikátu.  
  
- Od skupiny ve vaší organizaci, která je odpovědná za vytváření digitálních certifikátů, můžete získat jednu ze skupiny.  
  
- Vygenerujte vlastní certifikát pomocí nástroje MakeCert. exe, který je součástí [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Jak používání certifikačních autorit pomáhá uživatelům  
 Certifikát generovaný pomocí nástroje MakeCert. exe se často označuje jako certifikát pro *certifikáty nebo* *testování*. Tento druh certifikátu funguje podobně jako soubor. snk v .NET Framework. Skládá se výhradně z páru veřejného a soukromého kryptografického klíče a neobsahuje žádné ověřitelné informace o vydavateli. Certifikáty můžete použít k nasazení aplikací [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] s vysokou důvěryhodností na intranetu. Pokud jsou však tyto aplikace spuštěny v klientském počítači, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je budou identifikovat jako pocházející od neznámého vydavatele. Ve výchozím nastavení nemůžou aplikace [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] podepsané pomocí vlastních certifikátů a nasazené přes Internet využívat nasazení důvěryhodných aplikací.  
  
 Naopak pokud obdržíte certifikát od certifikační autority, jako je například dodavatel certifikátu nebo oddělení v rámci podniku, certifikát nabízí větší zabezpečení pro vaše uživatele. Neidentifikuje pouze vydavatele podepsaného softwaru, ale ověřuje tuto identitu tím, že zkontroluje certifikační autoritu, která ho podepsala. Pokud certifikační autorita není kořenovou autoritou, technologie Authenticode se také "řetězit" zpět k kořenové autoritě a ověří, zda je certifikační autorita autorizována k vydávání certifikátů. Pro zajištění vyššího zabezpečení byste měli použít certifikát vydaný certifikační autoritou, kdykoli to bude možné.  
  
 Další informace o generování vlastních certifikátů najdete v tématu [Makecert. exe (Nástroj pro vytváření certifikátů)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Časová razítka  
 Certifikáty používané k podepisování aplikací [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vyprší po určité době, většinou dvanáct měsíců. Aby bylo možné odstranit nutnost nepřetržitě znovu podepisovat aplikace pomocí nových certifikátů, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] podporuje časové razítko. Pokud je aplikace podepsána pomocí časového razítka, její certifikát bude nadále přijat i po vypršení platnosti, pokud je časové razítko platné. To umožňuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacím s certifikáty s vypršenou platností, ale s platnými časovými razítky ke stažení a spuštění. Umožňuje taky nainstalované aplikace s certifikáty s vypršenou platností, aby bylo možné dál stahovat a instalovat aktualizace.  
  
 Chcete-li zahrnout časové razítko na aplikační server, musí být k dispozici server časového razítka. Informace o tom, jak vybrat server časových razítek, naleznete v tématu [How to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Aktualizace certifikátů s vypršenou platností  
 V dřívějších verzích .NET Framework mohla aktualizace aplikace, jejíž certifikát vypršel, způsobit, že aplikace přestane fungovat. Chcete-li tento problém vyřešit, použijte jednu z následujících metod:  
  
- Aktualizujte .NET Framework na verzi 2,0 SP1 nebo novější v systému Windows XP nebo verze 3,5 nebo novější v systému Windows Vista.  
  
- Odinstalujte aplikaci a znovu nainstalujte novou verzi s platným certifikátem.  
  
- Vytvořte sestavení příkazového řádku, které aktualizuje certifikát. Podrobné informace o tomto procesu najdete na [Podpora Microsoftu článku 925521](https://support.microsoft.com/kb/925521).  
  
### <a name="storing-certificates"></a>Ukládání certifikátů  
  
- Certifikáty můžete ukládat jako soubor. pfx v systému souborů, nebo je můžete uložit do kontejneru klíčů. Uživatel v doméně systému Windows může mít několik kontejnerů klíčů. Nástroj MakeCert. exe ve výchozím nastavení uloží certifikáty do kontejneru osobních klíčů, pokud nezadáte, že by ho místo toho měl Uložit do souboru. pfx. Mage. exe a MageUI. exe, [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] nástroje pro vytváření nasazení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], umožňují používat certifikáty uložené v libovolném způsobem.  
  
## <a name="see-also"></a>Viz také  
   [zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)  
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
