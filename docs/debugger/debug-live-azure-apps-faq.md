---
title: Nejčastější dotazy k ladění snímků | Microsoft Docs
description: Projděte si seznam nejčastějších dotazů, které se mohou zobrazit při ladění živých aplikací Azure pomocí Snapshot Debugger v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9bd8a80f7f6d11587c9f0cd5c6b9bf96e38a0a74
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800480"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Nejčastější dotazy k ladění snímků v aplikaci Visual Studio

Tady je seznam otázek, které se můžou zobrazit při ladění živých aplikací Azure pomocí Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Jaké jsou náklady na výkon při pořízení snímku?

Když Snapshot Debugger zachytí snímek aplikace, rozvětvení zpracuje proces aplikace a pozastaví rozvětvenou kopii. Při ladění snímku budete ladit proti rozvětvené kopii procesu. Tento proces trvá jenom 10-20 milisekund, ale nekopíruje celou haldu aplikace. Místo toho zkopíruje pouze stránku tabulky a nastaví stránky pro kopírování při zápisu. Pokud se některé objekty vaší aplikace v haldě změní, jejich příslušné stránky se zkopírují. Tato Syrovátka má každý snímek za malý objem paměti (v pořadí stovek kilobajtů pro většinu aplikací).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Co se stane, když mám Azure App Service s horizontálním škálováním (více instancí mojí aplikace)?

Pokud máte více instancí aplikace, snímkovací body se aplikuje na každou jednu instanci. Pouze první snímkovací bod, který se má vysáhnout se zadanými podmínkami vytvoří snímek. Pokud máte více snímkovací body, pozdější snímky pocházejí ze stejné instance, která vytvořila první snímek. Protokolovacích bodů odeslané do okna výstup bude zobrazovat pouze zprávy z jedné instance, zatímco protokolovacích bodů odesílání do protokolů aplikací odesílá zprávy ze všech instancí.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Jak Snapshot Debugger načte symboly?

Snapshot Debugger vyžaduje, abyste měli odpovídající symboly pro vaši aplikaci buď místně, nebo nasazené do Azure App Service. (Vložené soubory PDB se v tuto chvíli nepodporují.) Snapshot Debugger automaticky stáhne symboly z vašeho Azure App Service. Počínaje verzí Visual Studio 2017 verze 15,2, nasazení pro Azure App Service také nasadí symboly vaší aplikace.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Funguje Snapshot Debugger proti sestavením vydání mé aplikace?

Ano – Snapshot Debugger má fungovat se sestaveními verzí. Když je ve funkci umístěný bod snappointu, funkce se znovu zkompiluje zpět na ladicí verzi, takže ji lze ladit. Zastavení Snapshot Debugger vrátí funkce do verze sestavení verze.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Mohou protokolové body způsobovat vedlejší účinky v produkční aplikaci?

Ne – všechny zprávy protokolu, které přidáte do aplikace, se vyhodnotí virtuálně. Nemůže způsobit žádné vedlejší účinky vaší aplikace. Některé nativní vlastnosti však nemusí být přístupné pomocí protokolových bodů.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Funguje Snapshot Debugger zatížení serveru?

Ano, ladění snímků může fungovat u serverů při zatížení. Funkce Snapshot Debugger ohrorizuje a nezachycuje snímky v situacích, kdy je na vašem serveru málo volného místa.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Návody odinstalovat Snapshot Debugger?

Rozšíření lokality Snapshot Debugger na počítači můžete App Service pomocí následujících kroků:

1. Vypněte svůj App Service prostřednictvím Průzkumníka cloudu v Visual Studio nebo Azure Portal.
1. Přejděte na App Service Kudu vašeho uživatele (to znamená yourappservice).**scm**.azurewebsites.net) a přejděte na **Rozšíření webu**.
1. Kliknutím na X v Snapshot Debugger lokality ho odeberte.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Proč jsou porty otevřené během Snapshot Debugger relace?

Snapshot Debugger k ladění snímků pořízených v Azure je potřeba otevřít sadu portů, jedná se o stejné porty vyžadované pro vzdálené ladění. [Seznam portů najdete tady.](../debugger/remote-debugger-port-assignments.md)

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Návody rozšíření vzdáleného ladicího programu zakázat?

Pro App Services:
1. Zakažte rozšíření vzdáleného ladicího programu prostřednictvím Azure Portal pro vaši App Service.
2. Azure Portal > okno prostředků služby Application Service > *nastavení aplikace*
3. Přejděte do části *ladění* a klikněte na tlačítko *vypnout* pro *vzdálené ladění*.

Pro AKS:
1. Aktualizujte souboru Dockerfile tak, aby se odebraly oddíly odpovídající [Visual Studio Snapshot Debugger v imagích Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Znovu sestavte a nasaďte upravenou image Docker.

V případě virtuálních počítačů nebo virtuálních počítačů můžete odebrat rozšíření vzdáleného ladícího programu, certifikáty, trezory klíčů a příchozí fondy NAT následujícím způsobem:

1. Odebrat rozšíření vzdáleného ladicího programu

   Existuje několik způsobů, jak zakázat vzdálený ladicí program pro virtuální počítače a sady škálování virtuálních počítačů:

      - Zakázání vzdáleného ladicího programu přes Průzkumníka cloudu

         - Průzkumník cloudu > prostředku virtuálního počítače > zakázat ladění (Zakázání ladění pro sadu škálování virtuálního počítače v Průzkumníkovi cloudu neexistuje).

      - Zakázání vzdáleného ladicího programu pomocí skriptů a rutin PowerShellu

         Pro virtuální počítač:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Pro Virtual Machine Scale Sets:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Zakázání vzdáleného ladicího programu pomocí Azure Portal
         - Azure Portal > > rozšíření pro virtuální počítač nebo virtuální počítač sady VM Scale Sets
         - Odinstalace rozšíření Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger

         > [!NOTE]
         > Virtual Machine Scale Sets – portál nepovoluje odebírání DebuggerListener portů. Budete muset použít Azure PowerShell. Podrobnosti najdete níže.

2. Odebrání certifikátů a Azure KeyVault

   Při instalaci rozšíření vzdáleného ladicího programu pro virtuální počítač nebo škálovací sady virtuálních počítačů se vytvoří certifikáty klienta i serveru k ověření klienta Visual Studio pomocí prostředků škálovací sady virtuálních počítačů Azure nebo virtuálních počítačů.

   - Klientský certifikát

      Tento certifikát je certifikát podepsaný svým držitelem umístěný v cert:/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Jeden ze způsobu odebrání tohoto certifikátu z počítače je prostřednictvím PowerShellu.

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Certifikát serveru
      - Odpovídající kryptografický otisk certifikátu serveru se nasadí jako tajný kód do služby Azure KeyVault. Visual Studio se pokusí najít nebo vytvořit trezor klíčů s předponou MSVSAZ* v oblasti odpovídající prostředku virtuálního počítače nebo škálovací sady virtuálních počítačů. Všechny prostředky virtuálních počítačů nebo škálovací sady virtuálních počítačů nasazené do této oblasti proto budou sdílet stejnou trezor klíčů KeyVault.
      - Pokud chcete odstranit tajný klíč kryptografického otisku certifikátu serveru, přejděte do Azure Portal a vyhledejte trezor klíčů MSVSAZ* ve stejné oblasti, která je hostitelem vašeho prostředku. Odstraňte tajný kód, který by měl být označený popiskem. `remotedebugcert<<ResourceName>>`
      - Budete také muset odstranit tajný klíč serveru z vašeho prostředku prostřednictvím PowerShellu.

      Pro virtuální počítače:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Pro škálovací sady virtuálních počítačů:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Odeberte všechny fondy naslouchacího procesu DebuggerListener InBound NAT (jenom škálovací sada virtuálních počítačů).

   Vzdálený ladicí program zavádí fondy NAT svázané s DebuggerListener, které se použijí na nástroj pro vyrovnávání zatížení vaší škálovací sady.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Návody zakázat Snapshot Debugger?

Pro App Service:
1. Zakažte Snapshot Debugger prostřednictvím Azure Portal pro váš App Service.
2. Azure Portal > okno prostředků služby Application Service > *nastavení aplikace*
3. V Azure Portal odstraňte následující nastavení aplikace a uložte provedené změny.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Všechny změny nastavení aplikace spustí restart aplikace. Další informace o nastavení aplikace najdete v tématu [Konfigurace aplikace App Service v Azure Portal](/azure/app-service/web-sites-configure).

Pro AKS:
1. Aktualizujte souboru Dockerfile tak, aby se odebraly oddíly odpovídající [Visual Studio Snapshot Debugger v imagích Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Znovu sestavte a nasaďte upravenou image Docker.

Pro virtuální počítače/sady škálování virtuálních počítačů:

K dispozici je několik způsobů, jak Snapshot Debugger zakázat:
- Průzkumník cloudu > prostředku virtuálního počítače/sady škálování virtuálního počítače > zakázat diagnostiku

- Azure Portal > v okně prostředků virtuálního počítače nebo virtuálního počítače > rozšíření > Odinstalace rozšíření Microsoft. Insights. VMDiagnosticsSettings

- Rutiny PowerShellu z [AZ PowerShell](/powershell/azure/overview)

   Virtuální počítač:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Sady škálování virtuálních počítačů:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [Ladění živých aplikací ASP.NET pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Ladění živých ASP.NET počítačů Azure Virtual Machines\Virtual pro škálování pomocí Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Ladění Live ASP.NET Azure Kubernetes pomocí Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Řešení potíží a známé problémy pro ladění snímků](../debugger/debug-live-azure-apps-troubleshooting.md)
