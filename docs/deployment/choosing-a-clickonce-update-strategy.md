---
title: Výběr strategie aktualizace ClickOnce | Microsoft Docs
description: Přečtěte si, jak aplikace ClickOnce podporuje automatické aktualizace a jaké strategie aktualizace můžete použít.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d546b48ffbbb4d44fb5f2ced11f41826370403e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895073"
---
# <a name="choose-a-clickonce-update-strategy"></a>Výběr strategie aktualizace ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] může poskytovat automatické aktualizace aplikací. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Aplikace pravidelně čte soubor manifestu nasazení a zjistí, zda jsou k dispozici aktualizace aplikace. Pokud je k dispozici nová verze aplikace, je stažena a spuštěna. Z důvodu efektivity budou staženy pouze soubory, které byly změněny.

 Při navrhování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace je třeba určit strategii, kterou bude aplikace používat ke kontrole dostupných aktualizací. Můžete použít tři základní strategie: kontrolu aktualizací při spuštění aplikace, kontrolu aktualizací po spuštění aplikace (spuštěno jako vlákno na pozadí) nebo poskytnutí uživatelského rozhraní pro aktualizace.

 Kromě toho můžete určit, jak často bude aplikace aktualizace vyhledávat, a aktualizace můžete nastavit jako povinné.

> [!NOTE]
> Aktualizace aplikace vyžadují připojení k síti. Pokud není k dispozici síťové připojení, bude aplikace spuštěna bez kontroly aktualizací, bez ohledu na vybranou strategii aktualizace.

> [!NOTE]
> V .NET Framework 2,0 a .NET Framework 3,0 vždy, když aplikace kontroluje aktualizace, před nebo po spuštění nebo pomocí \<xref:System.Deployment.Application> rozhraní API, je nutné nastavit `deploymentProvider` v manifestu nasazení. `deploymentProvider`Element v aplikaci Visual Studio odpovídá poli **umístění aktualizace** v dialogovém okně **aktualizace** na kartě **publikovat** . Toto pravidlo je uvolněno v .NET Framework 3,5. Další informace najdete v tématu [nasazení aplikací ClickOnce pro testovací a provozní servery bez nutnosti opětovného podepsání](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

## <a name="check-for-updates-after-application-startup"></a>Po spuštění aplikace vyhledat aktualizace
 Pomocí této strategie se aplikace pokusí po spuštění vyhledat a přečíst soubor manifestu nasazení na pozadí. Pokud je k dispozici aktualizace, bude při dalším spuštění aplikace uživatel vyzván ke stažení a instalaci aktualizace.

 Tato strategie je nejvhodnější pro síťová připojení s nízkou šířkou pásma nebo v případě větších aplikací, které mohou vyžadovat dlouhé stahování.

 Chcete-li povolit tuto strategii aktualizace, klikněte na tlačítko **po spuštění aplikace** v části **Vyberte, kdy má aplikace vyhledávat aktualizace** v dialogovém okně **aktualizace aplikace** . Pak zadejte interval aktualizace v části určete, **jak často by měla aplikace vyhledávat aktualizace**.

 To je totéž jako změna elementu **Update** v manifestu nasazení následujícím způsobem:

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <expiration maximumAge="6" unit="hours" />
   </update>
</subscription>
```

## <a name="check-for-updates-before-application-startup"></a>Vyhledat aktualizace před spuštěním aplikace
 Výchozí strategií je vyhledání a přečtení souboru manifestu nasazení před spuštěním aplikace. Pomocí této strategie se aplikace pokusí vyhledat a přečíst soubor manifestu nasazení pokaždé, kdy uživatel spustí aplikaci. Pokud je k dispozici aktualizace, bude stažena a spuštěna; v opačném případě bude spuštěna stávající verze aplikace.

 Tato strategie je nejvhodnější pro síťová připojení s velkou šířkou pásma; zpoždění při spouštění aplikace může být v případě připojení s nízkou šířkou pásma nepřijatelně dlouhé.

 Chcete-li povolit tuto strategii aktualizace, klikněte na tlačítko **před spuštěním aplikace** v části **Vyberte, kdy má aplikace vyhledat aktualizace** v dialogovém okně **aktualizace aplikace** .

 To je totéž jako změna elementu **Update** v manifestu nasazení následujícím způsobem:

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <beforeApplicationStartup />
   </update>
</subscription>
```
> [!NOTE]
> U .NET 3,1 a novějších aplikací kontroluje aktualizace před spuštěním aplikace jedinou podporovanou možnost aktualizace.

## <a name="make-updates-required"></a>Nastavit požadované aktualizace
 Mohou nastat situace, kdy požadujete, aby uživatelé spouštěli aktualizovanou verzi aplikace. Například můžete provést změnu externího prostředku, jako jsou webové služby, které by omezily správnou funkčnost starší verze aplikace. V tomto případě budete pravděpodobně chtít nastavit aktualizaci jako povinnou a zabránit uživatelům ve spouštění starší verze.

> [!NOTE]
> I když můžete vyžadovat aktualizace pomocí dalších strategií aktualizace, kontrola před spuštěním **aplikace** je jediným způsobem, jak zaručit, že se starší verze nedá spustit. Pokud je při spuštění zjištěna povinná aktualizace, musí uživatel aktualizaci přijmout, nebo musí aplikaci ukončit.

 Chcete-li aktualizaci označit jako povinnou, klikněte v dialogovém okně **aktualizace aplikace** na možnost **zadat minimální požadovanou verzi této aplikace** a pak zadejte verzi publikování (**hlavní**, **podverze,** **sestavení**, **Revize**), která určuje nejnižší číslo verze aplikace, kterou lze nainstalovat.

 To je stejné jako nastavení atributu **určovat minimumRequiredVersion** elementu **nasazení** v manifestu nasazení; například:

```xml
<deployment install="true" minimumRequiredVersion="1.0.0.0">
```

## <a name="specify-update-intervals"></a>Zadat intervaly aktualizace
 Můžete také určit, jak často bude aplikace ověřovat aktualizace. Chcete-li toto nastavení provést, zadejte, aby aplikace vyhledávala aktualizace po spuštění, jak je popsáno v oddílu „Kontrola aktualizací po spuštění aplikace“ výše v tomto tématu.

 Chcete-li zadat interval aktualizace, nastavte v dialogovém okně **aktualizace aplikace** **Určete, jak často by měla aplikace vyhledávat aktualizace** vlastností.

 To je stejné jako nastavení **maximálního** počtu a atributů **jednotek** elementu **Update** v manifestu nasazení.

 Kontrolu můžete provádět například při každém spuštění aplikace, nebo jedenkrát za týden, nebo jednou za měsíc. Pokud v určený čas není k dispozici síťové připojení, provádí se kontrola aktualizace při příštím spuštění aplikace.

## <a name="provide-a-user-interface-for-updates"></a>Zadání uživatelského rozhraní pro aktualizace
 Při používání této strategie poskytne vývojář aplikace uživatelské rozhraní, které umožňuje uživateli zvolit, kdy nebo jak často bude aplikace vyhledávat aktualizace. Můžete například vytvořit příkaz „Zkontrolovat aktualizace nyní“ nebo dialogové okno „Nastavení aktualizací“ s možnostmi pro různé intervaly aktualizací. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Rozhraní API pro nasazení poskytují rozhraní pro programování vlastního uživatelského rozhraní aktualizace. Další informace najdete v tématu <xref:System.Deployment.Application> obor názvů.

 Pokud aplikace používá rozhraní API nasazení pro řízení vlastní logiky aktualizací, měli byste zablokovat kontrolu aktualizací podle postupu popsaného v části „Blokování kontroly aktualizací“ v následujícím oddílu.

 Tato strategie funguje nejlépe tehdy, pokud požadujete různé strategie aktualizací pro různé uživatele.

## <a name="block-update-checking"></a>Zablokovat kontrolu aktualizací
 Kontrolu aktualizací lze také kompletně zrušit. Například můžete mít jednoduchou aplikaci, která nebude nikdy aktualizována, ale chcete využít výhod snadné instalace, kterou poskytuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení.

 Měli byste také blokovat kontrolu aktualizací, pokud vaše aplikace používá rozhraní API pro nasazení k provádění vlastních aktualizací. Viz část "poskytnutí uživatelského rozhraní pro aktualizace" výše v tomto tématu.

 Chcete-li zablokovat kontrolu aktualizací, zrušte zaškrtnutí políčka **aplikace by měla vyhledávat aktualizace** v dialogovém okně aktualizace aplikace.

 Kontrolu aktualizací můžete také zablokovat odebráním `<Subscription>` značky z manifestu nasazení.

## <a name="permission-elevation-and-updates"></a>Zvýšení úrovně oprávnění a aktualizace
 Pokud nová verze [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace vyžaduje vyšší úroveň důvěryhodnosti, než je předchozí verze, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vyzve uživatele, aby k aplikaci udělil tuto vyšší úroveň důvěryhodnosti. Pokud uživatel odmítne udělit vyšší úroveň důvěryhodnosti, nebude aktualizace nainstalována. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vyzve uživatele k instalaci aplikace znovu při příštím restartování. Pokud uživatel v tomto kroku odmítne udělit vyšší úroveň důvěryhodnosti a aktualizace není označena jako povinná, bude spuštěna starší verze aplikace. Pokud je však aktualizace vyžadována, aplikace se nespustí, dokud uživatel nepřijme vyšší úroveň důvěryhodnosti.

 Pokud použijete nasazení důvěryhodné aplikace, nebude tato výzva týkající se úrovně důvěryhodnosti zobrazena. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).

## <a name="see-also"></a>Viz také
- <xref:System.Deployment.Application>
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Jak ClickOnce provádí aktualizaci aplikací](../deployment/how-clickonce-performs-application-updates.md)
- [Postupy: Správa aktualizací pro aplikaci ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)
