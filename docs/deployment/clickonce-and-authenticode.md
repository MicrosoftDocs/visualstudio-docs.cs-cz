---
title: ClickOnce a Authenticode | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0920da406e911f388c2b9ae77db16ee325aaae65
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806972"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce a kód Authenticode
*Authenticode* je technologie Microsoftu, která používá standardní kryptografii pro podepsání kódu aplikace digitálními certifikáty, které ověřují pravost vydavatele aplikace. Pomocí technologie Authenticode pro nasazení aplikací [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] snižuje riziko trojského koně. Trojský kůň je Vir nebo jiný škodlivý program, který škodlivá třetí strana nepředstavuje legitimní program pocházející z vytvořeného důvěryhodného zdroje. Podepisování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení pomocí digitálního certifikátu je volitelný krok k ověření, že sestavení a soubory nejsou úmyslně poškozeny.

 Následující části popisují různé typy digitálních certifikátů používaných v technologii Authenticode, způsob ověřování certifikátů pomocí certifikačních autorit (CA), role časového razítka v certifikátech a metody úložiště dostupné pro certifikáty.

## <a name="authenticode-and-code-signing"></a>Technologie Authenticode a podepisování kódu
 *Digitální certifikát* je soubor, který obsahuje kryptografický pár veřejného a privátního klíče, spolu s metadaty, které popisují vydavatele, kterým byl certifikát vystavený, a agenturou, která certifikát vystavila.

 Existují různé typy certifikátů technologie Authenticode. Každá z nich je nakonfigurována pro různé typy podepisování. Pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace musíte mít certifikát Authenticode, který je platný pro podepisování kódu. Pokud se pokusíte podepsat aplikaci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] s jiným typem certifikátu, například digitálním e-mailovým certifikátem, nebude to fungovat. Další informace najdete v tématu [Úvod do podepisování kódu](/windows/desktop/seccrypto/cryptography-tools).

 Certifikát pro podepsání kódu můžete získat jedním ze tří způsobů:

- Zakupte si ho od dodavatele certifikátu.

- Od skupiny ve vaší organizaci, která je odpovědná za vytváření digitálních certifikátů, můžete získat jednu ze skupiny.

- Vygenerujte vlastní certifikát pomocí rutiny New-SelfSignedCertificate prostředí PowerShell nebo pomocí nástroje *Makecert. exe*, který je součástí [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].

### <a name="how-using-certificate-authorities-helps-users"></a>Jak používání certifikačních autorit pomáhá uživatelům
 Certifikát generovaný pomocí New-SelfSignedCertificate nebo nástroje *Makecert. exe* se často označuje jako certifikát s certifikátem *držitele* nebo *testu*. Tento druh certifikátu funguje podobně jako soubor *. snk* v .NET Framework. Skládá se výhradně z páru veřejného a soukromého kryptografického klíče a neobsahuje žádné ověřitelné informace o vydavateli. Certifikáty můžete použít k nasazení aplikací [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] s vysokou důvěryhodností na intranetu. Pokud jsou však tyto aplikace spuštěny v klientském počítači, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] je budou identifikovat jako pocházející od neznámého vydavatele. Ve výchozím nastavení nemůžou aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podepsané pomocí vlastních certifikátů a nasazené přes Internet využívat nasazení důvěryhodných aplikací.

 Naopak pokud obdržíte certifikát od certifikační autority, jako je například dodavatel certifikátu nebo oddělení v rámci podniku, certifikát nabízí větší zabezpečení pro vaše uživatele. Neidentifikuje pouze vydavatele podepsaného softwaru, ale ověřuje tuto identitu tím, že zkontroluje certifikační autoritu, která ho podepsala. Pokud certifikační autorita není kořenovou autoritou, technologie Authenticode se také "řetězit" zpět k kořenové autoritě a ověří, zda je certifikační autorita autorizována k vydávání certifikátů. Pro zajištění vyššího zabezpečení byste měli použít certifikát vydaný certifikační autoritou, kdykoli to bude možné.

 Další informace o generování vlastních certifikátů najdete v tématu [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) nebo [Makecert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Časová razítka
 Certifikáty používané k podepisování aplikací [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vyprší po určité době, většinou dvanáct měsíců. Aby bylo možné odstranit nutnost nepřetržitě znovu podepisovat aplikace pomocí nových certifikátů, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podporuje časové razítko. Pokud je aplikace podepsána pomocí časového razítka, její certifikát bude nadále přijat i po vypršení platnosti, pokud je časové razítko platné. To umožňuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacím s certifikáty s vypršenou platností, ale s platnými časovými razítky ke stažení a spuštění. Umožňuje taky nainstalované aplikace s certifikáty s vypršenou platností, aby bylo možné dál stahovat a instalovat aktualizace.

 Chcete-li zahrnout časové razítko na aplikační server, musí být k dispozici server časového razítka. Informace o tom, jak vybrat server časových razítek, naleznete v tématu [How to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Aktualizace certifikátů s vypršenou platností
 V dřívějších verzích .NET Framework mohla aktualizace aplikace, jejíž certifikát vypršel, způsobit, že aplikace přestane fungovat. Chcete-li tento problém vyřešit, použijte jednu z následujících metod:

- Aktualizujte .NET Framework na verzi 2,0 SP1 nebo novější v systému Windows XP nebo verze 3,5 nebo novější v systému Windows Vista.

- Odinstalujte aplikaci a znovu nainstalujte novou verzi s platným certifikátem.

- Vytvořte sestavení příkazového řádku, které aktualizuje certifikát. Podrobné informace o tomto procesu najdete na [Podpora Microsoftu článku 925521](https://support.microsoft.com/help/925521).

### <a name="store-certificates"></a>Uložení certifikátů

- Certifikáty můžete ukládat jako soubor *. pfx* v systému souborů, nebo je můžete uložit do kontejneru klíčů. Uživatel v doméně systému Windows může mít několik kontejnerů klíčů. Nástroj *Makecert. exe* ve výchozím nastavení uloží certifikáty do kontejneru osobních klíčů, pokud nezadáte, že by ho místo toho měl Uložit do souboru *. pfx* . *Mage. exe* a *MageUI. exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] nástroje pro vytváření nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], umožňují používat certifikáty uložené v libovolném způsobem.

## <a name="see-also"></a>Viz také:
- [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)
- [Zabezpečené aplikace ClickOnce](../deployment/securing-clickonce-applications.md)
- [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
