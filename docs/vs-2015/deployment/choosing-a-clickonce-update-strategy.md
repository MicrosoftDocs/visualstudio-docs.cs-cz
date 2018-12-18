---
title: Výběr strategie aktualizace ClickOnce | Dokumentace Microsoftu
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
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2ed97cecb01a8e42a01a3e358ecc953857ca55b6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191344"
---
# <a name="choosing-a-clickonce-update-strategy"></a>Výběr strategie aktualizace ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] může poskytovat automatické aktualizace aplikace. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace pravidelně čte soubor manifestu nasazení, pokud chcete zobrazit, zda jsou k dispozici aktualizace aplikace. Pokud je k dispozici nová verze aplikace, je stažena a spuštěna. Z důvodu efektivity budou staženy pouze soubory, které byly změněny.  
  
 Při navrhování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, je nutné určit strategii, kterou aplikace bude používat pro kontrolu dostupných aktualizací. Můžete použít tři základní strategie: kontrolu aktualizací při spuštění aplikace, kontrolu aktualizací po spuštění aplikace (spuštěno jako vlákno na pozadí) nebo poskytnutí uživatelského rozhraní pro aktualizace.  
  
 Kromě toho můžete určit, jak často bude aplikace aktualizace vyhledávat, a aktualizace můžete nastavit jako povinné.  
  
> [!NOTE]
>  Aktualizace aplikace vyžadují připojení k síti. Pokud není k dispozici síťové připojení, bude aplikace spuštěna bez kontroly aktualizací, bez ohledu na vybranou strategii aktualizace.  
  
> [!NOTE]
>  V rozhraní .NET Framework 2.0 a .NET Framework 3.0, kdykoli aplikace vyhledá aktualizace, před nebo po spuštění nebo pomocí <xref:System.Deployment.Application> rozhraní API, je nutné nastavit `deploymentProvider` v manifestu nasazení. `deploymentProvider` Odpovídající element v sadě Visual Studio **aktualizovat umístění** pole na **aktualizace** dialogovému oknu **publikovat** kartu. Toto pravidlo je v rozhraní .NET Framework 3.5 volné. Další informace najdete v tématu [nasazení ClickOnce aplikace pro testování a produkční servery bez Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
## <a name="checking-for-updates-after-application-startup"></a>Kontrola aktualizací po spuštění aplikace  
 Pomocí této strategie se aplikace pokusí po spuštění vyhledat a přečíst soubor manifestu nasazení na pozadí. Pokud je k dispozici aktualizace, bude při dalším spuštění aplikace uživatel vyzván ke stažení a instalaci aktualizace.  
  
 Tato strategie je nejvhodnější pro síťová připojení s nízkou šířkou pásma nebo v případě větších aplikací, které mohou vyžadovat dlouhé stahování.  
  
 Chcete-li povolit tuto strategii aktualizace, klikněte na tlačítko **po spuštění aplikace** v **Vyberte prosím, kdy by měla aplikace vyhledávat aktualizace** část **aktualizace aplikace** Dialogové okno. Potom zadejte interval aktualizace v části **zadejte, jak často by měla aplikace vyhledávat aktualizace**.  
  
 To je stejný jako v případě změny **aktualizace** manifest elementu v nasazení následujícím způsobem:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>Kontrola aktualizací před spuštěním aplikace  
 Výchozí strategií je vyhledání a přečtení souboru manifestu nasazení před spuštěním aplikace. Pomocí této strategie se aplikace pokusí vyhledat a přečíst soubor manifestu nasazení pokaždé, kdy uživatel spustí aplikaci. Pokud je k dispozici aktualizace, bude stažena a spuštěna; v opačném případě bude spuštěna stávající verze aplikace.  
  
 Tato strategie je nejvhodnější pro síťová připojení s velkou šířkou pásma; zpoždění při spouštění aplikace může být v případě připojení s nízkou šířkou pásma nepřijatelně dlouhé.  
  
 Chcete-li povolit tuto strategii aktualizace, klikněte na tlačítko **před spuštěním aplikace** v **Vyberte prosím, kdy by měla aplikace vyhledávat aktualizace** část **aktualizace aplikace** Dialogové okno.  
  
 To je stejný jako v případě změny **aktualizace** manifest elementu v nasazení následujícím způsobem:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>Nastavení povinných aktualizací  
 Mohou nastat situace, kdy požadujete, aby uživatelé spouštěli aktualizovanou verzi aplikace. Například můžete provést změnu externího prostředku, jako jsou webové služby, které by omezily správnou funkčnost starší verze aplikace. V tomto případě budete pravděpodobně chtít nastavit aktualizaci jako povinnou a zabránit uživatelům ve spouštění starší verze.  
  
> [!NOTE]
>  Ačkoli můžete aktualizace vyžadovat prostřednictvím jiných strategií pro aktualizace, kontrola **před spuštěním aplikace** je jediný způsob, jak zaručit, že nemůže být spuštěna starší verze. Pokud je při spuštění zjištěna povinná aktualizace, musí uživatel aktualizaci přijmout, nebo musí aplikaci ukončit.  
  
 K označení aktualizace jako povinné, klikněte na tlačítko **zadat minimální požadovanou verzi této aplikace** v **aplikace aktualizuje** dialogové okno a poté zadejte verzi publikování (**hlavní**, **Menší**, **sestavení**, **revize**), která určuje nejnižší číslo verze aplikace, která je možné nainstalovat.  
  
 Jedná se o stejné nastavení jako **minimumRequiredVersion** atribut **nasazení** elementu v manifestu nasazení; například:  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>Určení intervalů aktualizace  
 Můžete také určit, jak často bude aplikace ověřovat aktualizace. Chcete-li toto nastavení provést, zadejte, aby aplikace vyhledávala aktualizace po spuštění, jak je popsáno v oddílu „Kontrola aktualizací po spuštění aplikace“ výše v tomto tématu.  
  
 Chcete-li určit interval aktualizace, nastavte **zadejte, jak často by měla aplikace vyhledávat aktualizace** vlastnosti **aktualizace aplikace** dialogové okno.  
  
 Jedná se o stejné nastavení jako **maximumAge** a **jednotky** atributy **aktualizace** elementu v manifestu nasazení.  
  
 Kontrolu můžete provádět například při každém spuštění aplikace, nebo jedenkrát za týden, nebo jednou za měsíc. Pokud v určený čas není k dispozici síťové připojení, provádí se kontrola aktualizace při příštím spuštění aplikace.  
  
## <a name="providing-a-user-interface-for-updates"></a>Poskytování uživatelského rozhraní pro aktualizace  
 Při používání této strategie poskytne vývojář aplikace uživatelské rozhraní, které umožňuje uživateli zvolit, kdy nebo jak často bude aplikace vyhledávat aktualizace. Můžete například vytvořit příkaz „Zkontrolovat aktualizace nyní“ nebo dialogové okno „Nastavení aktualizací“ s možnostmi pro různé intervaly aktualizací. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Nasazení rozhraní API poskytují rámec pro programování vlastního uživatelského rozhraní aktualizací. Další informace najdete v tématu <xref:System.Deployment.Application> oboru názvů.  
  
 Pokud aplikace používá rozhraní API nasazení pro řízení vlastní logiky aktualizací, měli byste zablokovat kontrolu aktualizací podle postupu popsaného v části „Blokování kontroly aktualizací“ v následujícím oddílu.  
  
 Tato strategie funguje nejlépe tehdy, pokud požadujete různé strategie aktualizací pro různé uživatele.  
  
## <a name="blocking-update-checking"></a>Blokování kontroly aktualizací  
 Kontrolu aktualizací lze také kompletně zrušit. Například můžete mít jednoduchou aplikaci, která nebude nikdy aktualizována, ale budete chtít využít výhod snadné instalace poskytovanou [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení.  
  
 Pokud aplikace používá implementaci rozhraní API, měli byste rovněž zablokovat vlastní aktualizace v rámci této aplikace; viz oddíl „Poskytování uživatelského rozhraní pro aktualizace“ výše v tomto tématu.  
  
 Chcete-li blokovat kontrolu aktualizací, zrušte **by měla aplikace vyhledávat aktualizace** zaškrtávací políčko v dialogovém okně aktualizace aplikace.  
  
 Můžete taky zablokovat kontrolu tak, že odeberete aktualizací `<Subscription>` značky z manifestu nasazení.  
  
## <a name="permission-elevation-and-updates"></a>Zvýšení úrovně oprávnění a aktualizace  
 Pokud nová verze [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace vyžaduje vyšší úroveň důvěryhodnosti oproti předchozí verzi [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vyzve uživatele, pokud chce aplikaci udělit tuto vyšší úroveň důvěryhodnosti. Pokud uživatel odmítne udělit vyšší úroveň důvěryhodnosti, nebude aktualizace nainstalována. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vyzve uživatele k instalaci aplikace znovu při dalším restartování. Pokud uživatel v tomto kroku odmítne udělit vyšší úroveň důvěryhodnosti a aktualizace není označena jako povinná, bude spuštěna starší verze aplikace. Pokud je však aktualizace vyžadována, aplikace se nespustí, dokud uživatel nepřijme vyšší úroveň důvěryhodnosti.  
  
 Pokud použijete nasazení důvěryhodné aplikace, nebude tato výzva týkající se úrovně důvěryhodnosti zobrazena. Další informace najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Deployment.Application>   
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Jak ClickOnce provádí aktualizaci aplikací](../deployment/how-clickonce-performs-application-updates.md)   
 [Postupy: Správa aktualizací pro aplikaci ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)



