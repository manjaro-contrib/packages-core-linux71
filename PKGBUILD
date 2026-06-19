# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Archlinux maintainers:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

_basekernel=7.1
_basever=${_basekernel//.}
_kernelname=-MANJARO
_commit=
_rc=
pkgbase=linux${_basever}
pkgver=7.1.0
pkgrel=1
arch=('x86_64')
url="https://www.kernel.org/"
license=(GPL-2.0-only)
makedepends=(
  bc
  cpio
  gettext
  libelf
  pahole
  perl
  python
  rust
  rust-bindgen
  rust-src
  tar
  xz
)
options=(
  !debug
  !strip
)
source=(https://www.kernel.org/pub/linux/kernel/v7.x/linux-${_basekernel}.tar.xz
        #https://github.com/torvalds/linux/archive/refs/tags/v${_basekernel}.tar.gz
        #https://www.kernel.org/pub/linux/kernel/v7.x/patch-${pkgver}.xz
        config
        # Enable x86_64-v2 build optimisations
        more-ISA-levels-and-uarches-for-kernel-6.16+.patch
        # ARCH Patches
        0001-add-sysctl-to-disallow-unprivileged-CLONE_NEWUSER-by.patch
        0002-drivers-firmware-skip-simpledrm-if-nvidia-drm.modese.patch
        # Upstream Patches
        0000-drm-amdgpu-fix-race-condition-in-amdgpu_vm_wait_idle-during-process-kill.patch
        # Turn off custom brightness-curve when nonsense is found in BIOS
        0001-drm-amd-Sanity-check-custom-brightness-curve-data-po.patch
        # https://www.phoronix.com/news/AMD-Color-Management-Patches
        0000-amd-display-move-AMD_PRIVATE_COLOR-to-Kconfig.patch
        # From Valve for Upstream (fixes suspend on deck target in inputplumber)
        0000-usb-vhci-hcd-Unconditionally-allow-system-suspend.patch
        # https://invent.kde.org/plasma/kwin/-/merge_requests/9178
        # https://mail.kde.org/pipermail/distributions/2026-June/001711.html
        0001-udmabuf-Do-not-create-malformed-scatterlists.patch
        0002-udmabuf-fix-DMA-direction-mismatch-in-release_udmabuf.patch
        0003-udmabuf-skip-redundant-cpu-sync-to-fix-cach.patch
        # Manjaro Patches
        # Realtek patch
        0999-patch_realtek.patch
        # OGC patch-set
        # https://github.com/OpenGamingCollective/linux/tree/hphilm/        7.1/0-prep
        0001-FROM-ML-mmc-rtsx_pci_sdmmc-drop-MMC_CAP_AGGRESSIVE_P.patch
        0002-FROM-ML-misc-rtsx_pcr-prevent-pm_schedule_suspend-fo.patch
        0003-FROM-ML-mmc-rtsx_pci_sdmmc-increase-delay-after-powe.patch
        0004-FROM-ML-cgroup-dmem-Add-queries-for-protection-value.patch
        0005-FROM-ML-cgroup-cgroup-dmem-Add-dmem_-cgroup_common_a.patch
        0006-FROM-ML-drm-ttm-Extract-code-for-attempting-allocati.patch
        0007-FROM-ML-drm-ttm-Split-cgroup-charge-and-resource-all.patch
        0008-FROM-ML-drm-ttm-Be-more-aggressive-when-allocating-b.patch
        0009-FROM-ML-drm-ttm-Use-common-ancestor-of-evictor-and-e.patch
        0010-FROM-ML-drm-nouveau-Userspace-can-now-make-use-of-me.patch
        0011-FROM-ML-HID-hid-msi-Add-MSI-Claw-configuration-drive.patch
        0012-FROM-ML-HID-hid-msi-Add-M-key-mapping-attributes.patch
        0013-FROM-ML-HID-hid-msi-Add-RGB-control-interface.patch
        0014-FROM-ML-HID-hid-msi-Add-Rumble-Intensity-Attributes.patch
        0015-FROM-ML-HID-hid-oxp-Add-OneXPlayer-configuration-dri.patch
        0016-FROM-ML-HID-hid-oxp-Add-Second-Generation-RGB-Contro.patch
        0017-FROM-ML-HID-hid-oxp-Add-Second-Generation-Gamepad-Mo.patch
        0018-FROM-ML-HID-hid-oxp-Add-Button-Mapping-Interface.patch
        0019-FROM-ML-HID-hid-oxp-Add-Vibration-Intensity-Attribut.patch
        0020-FROM-ML-platform-x86-ayn-ec-Add-PWM-Fan-HWMON-Interf.patch
        0021-FROM-ML-platform-x86-ayn-ec-Add-Temperature-Sensors.patch
        0022-FROM-ML-platform-x86-ayn-ec-Add-RGB-Interface.patch
        0023-FROM-ML-platform-x86-ayn-ec-Add-AYN-EC-Platform-Docu.patch
        0024-FROM-ML-platform-x86-lenovo-wmi-other-Add-missing-CP.patch
        0025-FROM-ML-platform-x86-lenovo-wmi-other-Add-GPU-tunabl.patch
        0026-FROM-ML-platform-x86-lenovo-wmi-other-Rename-LWMI_OM.patch
        0027-FROM-ML-platform-x86-lenovo-wmi-other-Add-WMI-batter.patch
        0028-FROM-ML-platform-x86-lenovo-wmi-other-Add-force_load.patch
        0029-FROM-ML-platform-x86-lenovo-wmi-helpers-Add-helper-f.patch
        0030-FROM-ML-platform-x86-lenovo-wmi-capdata-Add-debugfs-.patch
        0031-EXTERNALLY-MAINTAINED-mfd-Add-MFD-core-driver-for-St.patch
        0032-EXTERNALLY-MAINTAINED-mfd-steamdeck-Expose-controlle.patch
        0033-EXTERNALLY-MAINTAINED-hwmon-Add-driver-for-Steam-Dec.patch
        0034-EXTERNALLY-MAINTAINED-hwmon-steamdeck-hwmon-Add-supp.patch
        0035-FROM-ML-platform-x86-asus-armoury-gate-PPT-writes-be.patch
        0036-FROM-ML-platform-x86-msi-wmi-Reformat-msi_wmi_notify.patch
        0037-FROM-ML-platform-x86-msi-wmi-Add-MSI-Claw-M-Center-k.patch
        0038-FROM-ML-platform-x86-msi-wmi-platform-Use-input-buff.patch
        0039-FROM-ML-platform-x86-msi-wmi-platform-Add-unlocked-m.patch
        0040-FROM-ML-platform-x86-msi-wmi-platform-Add-quirk-syst.patch
        0041-FROM-ML-platform-x86-msi-wmi-platform-Add-support-fo.patch
        0042-FROM-ML-platform-x86-msi-wmi-platform-Add-platform-p.patch
        0043-FROM-ML-platform-x86-msi-wmi-platform-Add-PL1-PL2-su.patch
        0044-FROM-ML-platform-x86-msi-wmi-platform-Add-charge_thr.patch
        0045-FROM-ML-platform-x86-msi-wmi-platform-Drop-excess-fa.patch
        0046-FROM-ML-platform-x86-msi-wmi-platform-Update-header-.patch
        0047-FROM-ML-platform-x86-msi-wmi-platform-Restore-fan-cu.patch
        0048-Revert-FROM-ML-HID-hid-msi-Add-Rumble-Intensity-Attr.patch
        0049-Revert-FROM-ML-HID-hid-msi-Add-RGB-control-interface.patch
        0050-Revert-FROM-ML-HID-hid-msi-Add-M-key-mapping-attribu.patch
        0051-Revert-FROM-ML-HID-hid-msi-Add-MSI-Claw-configuratio.patch
        0052-FROM-ML-HID-hid-msi-Add-MSI-Claw-configuration-drive.patch
        0053-FROM-ML-HID-hid-msi-Add-M-key-mapping-attributes.patch
        0054-FROM-ML-HID-hid-msi-Add-RGB-control-interface.patch
        0055-FROM-ML-HID-hid-msi-Add-Rumble-Intensity-Attributes.patch
        0056-FOR-UPSTREAM-hid-asus-ally-Add-joystick-LED-ring-sup.patch
        0057-FOR-UPSTREAM-hid-asus-ally-do-MCY-FW-validation-in-h.patch
        0058-FOR-UPSTREAM-hid-asus-ally-initial-Ally-X-gamepad-br.patch
        0059-FOR-UPSTREAM-hid-asus-ally-initial-gamepad-configura.patch
        0060-FOR-UPSTREAM-hid-asus-ally-add-button-remap-attribut.patch
        0061-FOR-UPSTREAM-hid-asus-ally-add-gamepad-mode-selectio.patch
        0062-FOR-UPSTREAM-hid-asus-ally-Turbo-settings-for-button.patch
        0063-FOR-UPSTREAM-hid-asus-ally-add-vibration-intensity-s.patch
        0064-FOR-UPSTREAM-hid-asus-ally-add-JS-deadzones.patch
        0065-FOR-UPSTREAM-hid-asus-ally-add-trigger-deadzones.patch
        0066-FOR-UPSTREAM-hid-asus-ally-add-anti-deadzones.patch
        0067-FOR-UPSTREAM-hid-asus-ally-add-JS-response-curves.patch
        0068-FOR-UPSTREAM-hid-asus-ally-mcu_version-attribute.patch
        0069-FOR-UPSTREAM-hid-asus-ally-add-calibrations-wip.patch
        0070-FOR-UPSTREAM-debug-by-default.patch
        0071-FOR-UPSTREAM-hid-asus-ally-grab-short-press-QAM-on-R.patch
        0072-FOR-UPSTREAM-hid-asus-ally-disable-wakeup-attribute-.patch
        0073-EXTERNALLY-MAINTAINED-drm-amd-display-Enable-3-overl.patch
        0001-NOT-FOR-UPSTREAM-platform-x86-msi-wmi-platform-Fix-i.patch
        # Gaming patches from CachyOS
        0003-leds-steamdeck-Add-support-for-Steam-Deck-LED.patch
        0008-Disable-modes-with-1200-MHz-Pixel-clocks-when-connec.patch
        0009-drm-amdgpu-Don-t-use-doorbells-for-SDMA-5.2.patch
        0010-Add-2s-delay-before-enabling-DP-link-for-dock.patch
        0011-drivers-video-backlight-Disable-backlight-notificati.patch
        0014-ASoC-max98388-Fix-power-on-when-resuming-from-suspen.patch
        0015-ASoC-amd-acp-Use-correct-DAI-link-ID-for-BT-codec.patch
        0016-wifi-ath11k-Rename-QCA2066-fw-dir-to-QCA206X.patch
        # HDMI VRR support https://github.com/Lawstorant/linux/tree/hdmi-7.1
        0001-drm-amd-display-Refactor-amdgpu_dm_update_freesync_c.patch
        0002-Do-not-modify-display_info-in-freesync_caps.patch
        0003-Modify-display-range-if-freesync-capable.patch
        0004-drm-amd-display-Remove-redundant-edid-checks.patch
        0005-drm-amd-display-Move-DisplayID-vrr-parsing.patch
        0006-drm-amd-display-Always-try-to-parse-AMD-vsdb.patch
        0007-drm-amd-display-Check-for-VRR-range-in-CEA-AMD-vsdb.patch
        0008-drm-amd-display-Use-bigger-VRR-range-if-found-in-AMD.patch
        0009-drm-amd-display-Separate-DP-eDP-and-PCON-paths-compl.patch
        0010-drm-amd-display-Refactor-PCON-VRR-compatibility-chec.patch
        0011-drm-amd-display-Add-PCON-VRR-ID-check-override.patch
        0012-drm-amd-display-Add-CH7218-PCON-ID.patch
        0013-drm-edid-Parse-more-info-from-HDMI-Forum-vsdb.patch
        0014-drm-amd-display-Rename-PCON-adaptive-sync-types.patch
        0015-drm-amd-display-Enable-HDMI-VRR-over-PCON.patch
        0016-drm-amd-display-Support-HDMI-VRRmax-0.patch
        0017-drm-amd-display-Build-HDMI-vsif-in-correct-slot.patch
        0018-drm-amd-display-Save-HDMI-gaming-info-to-edid-caps.patch
        0019-drm-amd-display-Restore-ALLM-support-in-HDMI-vsif.patch
        0020-drm-amd-display-Trigger-ALLM-if-it-s-available.patch
        0021-drm-amd-display-Reintroduce-VTEM-info-frame.patch
        0022-drm-amd-display-Enable-HDMI-VRR.patch
        0023-Merge-HDMI-and-PCON-paths.patch
        0024-drm-amd-display-freesync_on_desktop-support-for-HDMI.patch
        0025-Force-freesync_on_desktop-for-HDMI.patch
        0026-drm-Add-ALLM-properties-to-connector.patch
        0027-drm-amd-display-Use-ALLM-properties-in-amdgpu.patch
        0028-fixu.patch
        # Zotac Zone patches
        0001-zotac-zone-hid-initial-impl.patch
        0002-xpad-gate-the-zotac-zone-PID-behind-if-IS_REACHABLE-.patch
        0003-tmp-apply-zotac-screen-quirk.patch
        0005-zone-fix-6.15-rename-del_timer-to-timer_delete.patch
        # AMD patches
        # [PATCH v11] Add AMD ISP4 driver
        # https://patchew.org/linux/20260506093250.93460-1-Bin.Du@amd.com/
        0001-media-platform-amd-Introduce-amd-isp4-capture-driver.patch
        0002-media-platform-amd-low-level-support-for-isp4-firmware.patch
        0003-media-platform-amd-Add-isp4-fw-and-hw-interface.patch
        0004-media-platform-amd-isp4-subdev-and-firmware-loading-handling-added.patch
        0005-media-platform-amd-isp4-video-node-and-buffers-handling-added.patch
        0006-media-platform-amd-isp4-debug-fs-logging-and-more-descriptive-errors.patch
        0007-Documentation-add-documentation-of-AMD-isp-4-driver.patch
        #iwlwifi: Fix firmware version handling
        0000-iwlwifi-fix.patch
)

if [[ ! -z "$_commit" ]]; then
  _srcdir="linux-${_commit}"
elif [[ ! -z "$_rc" ]]; then
  _srcdir="linux-${_basekernel}-${_rc}"
else
  _srcdir="linux-${_basekernel}"
fi

sha256sums=('691f44797fbe790dc8a321604c927087526ad27b6d649925d60f8eed0a2564a0'
            '5f7d81bb5b34d694a1a2bbc8ee2593a42362d19f649bc358ce9630a396a3437d'
            '4d53324f7acbcf6eb1d85579c5b2c5d4504fab053001935ab1f3def7e0fb4b68'
            'e5e98d62b63704cecdf32dbe6a9bafea6e70b23fa8e01fe96ca220ac6036392e'
            'c21170eba77438abb8b8ab02aeccf16bfb2467a01303509945aa6b3a0fd16d31'
            '37f3222fafbe67dec3740933be37867e0c378468f71e9a6d5d6a07c2a2a568fe'
            'cacb08b2f43a9fd09053bffaacc4b7bdf8381772f26e61825fb696ded100af57'
            'ae19a89ac1a3852d08456e7d163baa30d8fc8bcb0e48d08aee1bc1549fb143ba'
            '512032c6b93fce24254da6cace7bf101c8f7c824761a0f99deed4b7724ac6f3e'
            'c3deec43967e5959135490b1bcf8bbe2a15f5c3a6c1675c06b5ed0031cbe1c04'
            '43dcb7be95a4c270dabe2660ef37212afa8bf1978530b1b9f9ea255caedacc51'
            'bcf73b329d7317a6eb4925fb8b7a781d10b244bf8392315b18da0648db00a8c5'
            '103688f3fceff664c919d94faab7a6948880710641110eaa71fe107ee06c37e9'
            'e6f60660e73225773fe72c0243e5d1d8279cd5abe3aa6e1e2311554dfc0bf965'
            '18e5460453b0bb97abd0bed65b8af913635752d2a1e3f9bc40055d6e33693df9'
            'f5d7b71f00e17a4c9b6fdd8195b292a4604bb90ca685c65f15032f9ad40050cb'
            '9b9c96a836deb72d67f654ca894d086d91de9f98aef49078b5e250db27c6ba45'
            'fea0e8c0123e3953be1d71ab593b0b66ffc2757751c990378039ee988eafa1f1'
            'dbc8345b488c1d77d1f446c8f1c8aab5a0b8f8f836b470d9708b3e70d171dc99'
            'd386f71ebaad6748e8add0f99612e14d82554180539d641c79f13d20cd011fc4'
            'e7edd2e2d7fdd60b217a975316ff819b904e856783cb34662dbcd8bde9e48e11'
            'e1a3c8f83afcaeb333d3a646c7ddcf6994b2a5cbb8ba0efc4c9851411b45a8dc'
            '48801f096dad21238929fff6770ab076a3986986289bb0d70beeb25175abf09e'
            '1424dcb3e5368aad8a738a5aab749f436a204c6b4b79cda88d57e9ba1521580f'
            '0e333dc06481e6ef7c0a5f60ffca4e4248bfc5d546767e8f3e1b069095f985a7'
            'f80de4febad948132120dcb293eabd3ef20f9b966147e683f31ec2d9303a4ac2'
            '664397b82df677a9dcfae2d2b4f92d0c550ef27c95803d3d9b052577968c5698'
            '84bc2f5a30105a3db6f4a4d3d28e769f25c56218e544acb4b909cedb98daf02c'
            'a8c621ebfba7020b0fe7eee45050349e586df9db88a2a27ad9a5977a25d59321'
            '56c9088fef0d157cf96b9a8e199894484684a2933906a48db12d2256c545b49b'
            '8f5edf8b2fb3bd98306c19a1f7dbe652a82e2c293046d5331ec68aa432e51fad'
            'cb8691119ee547734799b9855e8b0b32b8712db439ed4573d43ec600284d9c29'
            '43d345d9a9a1ef42feec29837ef3dcc343db1197d9859fdf5daf338698dd0c22'
            'f2b52d9bfc408ed9b69f02285455f443bba813a4ecacd9babad0b2cb89cc2dd1'
            '81b627dd52d26d32037ba5d861158bda5059684da425ffbc6e94adfe560a560f'
            'b16f7ae8603909de4e4aefb3a65a06993dd3c654745b0f6c92f8cb5f268aa2d7'
            'f11d2997403420cc296014c2ba4ca7fd312c5f4e650a6418edf60906509c6478'
            'b837a435f8ef5e3068f1091cb01706ebba918be93b114f1bae7a05a5020d846c'
            'dedf980f27c3dda3f391b4977eebb3839e24b40bbc60f290ed4ea71f75545aed'
            '85fdb312e021b58eccfdc730ab69aa5b5f3ef9021b6530ad24c904f45cdada34'
            '2cf4c2b558235efc7b5968ba8fc7bff029fee3f1df1571f927d0ebd918142ce9'
            '5c10a9283dec5a40ccf95913ae730acb2e9b953c296897b7738cd3db9de05d5a'
            '26f071b498b4b84b69256cd161693bbef2226d78997ce9f1b8f3a5bf60599813'
            '48cf6a83524ca51c283efa5b010b179116619598bda2bb155010a0adff6b4fd6'
            '395003dfd85886d3ed0b6762200c981a42871132a0c436844de6d08951861048'
            'c963fca75cc308f77e20299afde1cc57106c1487a0e458bd4481f00ac1f3417c'
            '28495aa39c301712d743530b888790d3ebcaae0b23778151651e4928418628af'
            '0351059980f36d0b5fd4d5a7ba6116469374fe6f7d60da16f5c199a2ba09579c'
            '03ac6ce458b95450f0f5bd923f7319c5e81c8ca21ed0659280f9d6d18b9d996e'
            'b8f05b439c41aba3e303a6575a6614f386afa889c07eafc5229614ef2d29cc2d'
            '2aeef52228083752040957bdcd6c4fdd0f3ff6b22c32a43e2310bd3fb60637e7'
            '7e77963ad2ccb3c7b5cfb320452e9fc5a7858963c17bf19bec275a5e2d0586ef'
            '616cfe49363576611b06f586aecc09ecd3244ef420abc9595e1f99135017d67b'
            '9cd318826c6634dae14599eac106acd40f48442d669c0dccb59fa4f31afc74a4'
            '56874a7def19131b5ee2517cd5321dba5bc9a94bd21f32155a629c86b66b4b13'
            'f93366d9379b0afda6ea34c30b096d480dc6602f527844bad1b7276ab183e3bf'
            'fc2b92a194bd9d09a4c85f298ef41138a0fc09825a7660ced177aec628fa457d'
            '3c1c790163c0bd70cac941297b34f1ab4c98ab62e90a97b581163106110a932d'
            'b39f6caf330464df5d80f3bd9338c6132a310b382e7958d3198c827678647c9e'
            '123b0439ffedd39861623597a20797c11b38f4b9a8b8a6e00a7f9df0c70e8c7c'
            'cdc2c51245a122414c0f26726a5de9e11e011222d9c020b36c44bb03b996fc07'
            '5003f4221de4fb21a6051a99421de53ed28ce89afe58ba69c739095cba66f75d'
            'ad7edbf1d78dc032d43cf10a80f39bb1fac574f797c7b47ba362ee9859b2da01'
            'ed1addd90902ebc7294b8c8aeac190828ef5378b2f4bd5d6bddebb973ac16084'
            'f93afc42e4e761033e6d5494ca7a2adfb2f630d7e7c03b4f63c04a74ba9db93e'
            '33033845eee2fbe8017bbdee7b8e66c24053715e30f93ef0b3cd4e723913fe33'
            '564a79d956c7dfd2bcefb464ed1d1c98442dd316dc83775799bd86b46fbdd0ab'
            '9aa1ddee79a1368ffb499b557ad123c92ec0120ba1d1379ddb9d560000033179'
            '9a50b3250163003c264713f7dfde302cd658ba4d36eb824a4a5293f3ff2cda54'
            '9c86a5439f28f6147d18ca524c7e3e249f725126dfca5a036145e8499aad9c5b'
            '3e3ea7cd668db9e7930813450549a39c4b2177f60c7f37a150347141ec5f237d'
            '17421bdc1b16ffa06391006c2c48960ff19accbf81714dbeea627dc17b50668b'
            '4a534cb849c9049282f6e4cb88643ba7eb02d2805b027afe290855459f2b7abd'
            '42974c895a9515d852a03678bc604aae3674543c964ce973edde2e35c1f2075a'
            '907ca312f17c1f1af203c50f12850e6697b51cf333d0c13764aad4182b2c2a1f'
            '92f9f2bddd351458c5658a981da306ebcee3b87d42351f214fd220bfcb84240b'
            '008b574350fa871979f400892fbe03e8f604be13c4a33ce5ae9e63b2c3aa79ee'
            '058803917507ced26fd186b3191c75196767fe3808ec83ef5645c4cf0f03d2ad'
            '54ec6b1eb398879daddd84a7b909586acd10e08ca4d39a8530f2401c1671c1bd'
            'd5908a7cc977fc554388cbe71bd9a72ac37c97f11eec62bc3781e154c9ad2911'
            '1a85bdbc3bf85aad5c22073b38c73f66ecf43d25be42c3c8615f80057efa1970'
            '6d06f97910b7df59b72057e9e4fbb96ed120c2045578950c1fa6be47a132014a'
            'ed75926df4930261ae336a4bd111031e3307e29c1ac8c1534b03878d69022bf5'
            '6e9c1413f110038a9085c98c296ccaf7568de565bbd4122c444559f4f4b67e92'
            'b831e786cba34a259d63da64e7cdb0237a6344bc9fca0d015736b686d3675472'
            '150d3ea199648b50de08de064b0ce759df8a4059eac9f53dbebf6c8821fb92e2'
            'd5e71c0271e2c459728fba1fa55346fc8f00c2cd283ad3083b42ae0fc7eca177'
            'c60d1d285d20dfb6353086cbe28ba5bbb593a85578bdba49ab46508d17b4b043'
            'd0e072a6052bca7bb226eb2217ab509bd79b76a95824032d96d19cbf59b0413b'
            '3afa225e99284a9c3aa91b0c88133b6de3cc79f4ad9d21833c72a6ae15add927'
            'f345f2e226d87e4d59b966fe6f1da597ea8f88262f723999394beae1169074aa'
            '5bc136d940f2a695c2758865bb4b14b617ee19db0604104f7809bae43479344b'
            '05468ccb20a963712c4cfde475db90625e6f464af7bc46d4fdd6ddf3e56dc482'
            '3902b6bb4f3e68e042596298684cbee224278a2f14cc56a71e0c53d28428f8bc'
            'ce21d041e62e353f1c733a5d952edb063ad7246b74e94979fc0cb32bbf7e4856'
            'b3e3bf41cc6976fe207ded9b0710575db53909b109cb50b246c163d9646b5593'
            '49d2a9a0f56b126d238e2917c4e93bfe7cde339e9680e72e7fb7fc50ea9d7ccc'
            '4f463a09ff32986199fa6c00848b6a72376edde036e8d1a7f3b31bc2302f2f43'
            'c3fbc66f60852aeca82b393d7b53dcc63d20562f9b386c96b1dc4a1068cff5e2'
            '0b8777b92735cbe88622c15ebfe1736f6a81cf879d05f63e98617ca3a2df3145'
            '659512f9cde05bda7d3e79a4ffc7afff1074c03d620e0537ad3cb1278e6c9b6d'
            '5deab2e9ad4c612e0bc15317fc108e7ade4407f329101fd9d77e3af79800f83d'
            '9405b647189b9dec51d82e069606eec616d26874738c6ec8abcdb751a83e41a7'
            'e7dce85ed79543392e97e02dd29a608ac87b1a801c065ee9c88bd8839e3f70ef'
            '518f842a72b6340216378067a2c9ff43482851baf0dd7a601697df0d90d6f295'
            'e8d36ab9fc3c20b597eef73c9602e196cf4376ba8ac5a899c51c8735c59d416b'
            'bcf1660d91aa71db67bedddc305c7f29eb7ceee7d8e358a5c306c9db68a570a9'
            '2d0cc32cef085d91f1a17553bf941de2a4c0ae6213b225b1dcf65aeaa14b7066'
            'c47bfa8b75539a48e82899182e4aa9410fcaeeedb85cde18290399523b166992'
            '286787adc6c04d72a4527b7bf3811947481857a25c61e6e92a6e80d1a0038432'
            'dc91322aba229d50313a2fb9b1659edc286b88e5a0b4234b016520240fae5148'
            '98ab310cc9210fad5a29a11c1cbf5d9dfd41c0059dec9cf6f273431f9dae3ce1'
            'eac0070df9b15cbf6926c8719f40936386e794337ccf3a909f4167f9eccddcf1'
            '74e5848da4dfb17aa071ca5c07a4fcb9d1ea667fc2974276e7afc1bc94bcf428'
            '18ffb4f8bedee9bbf4df41ebdad89aa78bd39d141120a8e227aea3f9936e4cc3'
            'ade9bd71c77d061514fe45fbcb57d86cac46d7ddc5ef84c8713386c0a27c5342'
            'a93d7ea6b3c4799201be2125ab60ba0620b2b8d8b9a66bda415c8b0fbe1b2074'
            '5ff27111c3d6ad6e5e49fcc9c569d32b318437b211269ab91021cb8e35ba26a6'
            '17a04e9b9e09b36ce884770685dca9dd5eb4e68567548c62e1b34c548f86e5de'
            'bcb0d16bed107415e87de355cc1f447e9bcd98afa6c5d1354c9ba3d0233823ab'
            '88faa1a49babb7fec1ed08ea7276e08b3dbf67494fd8e7fa8ac53c382fdbdfdb'
            '3342071c8f4d4b3dc54342d8affc8fcbae9cf4ce18b837fa07cb1be3db5342ed'
            '1a443ba16fab79a2f46406319093e8ce3ed4651ed29d528afcdbec5bfa8e1060'
            'b67f25c13e946b51712b0e828ebbf8bea980d339bd6effab17869f6a62e428df'
            'f53e0ad0892ab4bd85f55b4cbb829481eba28865cf835a46c80bc237e0771981'
            '138684588665b8f651dffb4e75c265a2b81f6bd7a606f75f8fc6814a4a63d3fd'
            '3d37e1f54290bad1b7a4c5c45046341dc4c1bfc2f8648b7754bf0bd9705b3a35'
            '934384a274e6b90c58f91ab1a7096e37bd85bc8c2fa5bc0aa37ed25def9840fe'
            '024f8903b4da69cee9c273aa15e4c1dea7e4c57f37c4c6e0936daf0a232676af'
            '83271e77f23648dbf1d282ee0630d4434820e509f3699dfc64f4c95913481a87'
            '9e095bb67f7583a6f61347272fcc64e85635868c8b08cc4f51882c5a9d9cd171'
            '13b898988272e7ccd2f51f67a0ccbc7be0759240bb04692473c418b0e61c8a88'
            '16a9d82e059303387aff4ea7cc5211bc50a71e39a99535f3d4f3af9bbec50426'
            'dc6412fd3b2defb700b71b4a287ec299d083d760ebdcb7d37b9928c273dd82be'
            '9628a67ac23beaf2de7194d2934386944adc64cb2a4a90e4c38b867b868654b4')

export KBUILD_BUILD_HOST=manjaro
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

prepare() {
  cd $_srcdir

  #msg "set PATCHLEVEL to 1"
  #sed -ri "s|^(PATCHLEVEL =).*|\1 1|" Makefile

  #msg "set EXTRAVERSION to ${_rc}"
  #sed -ri "s|^(EXTRAVERSION =).*|\1 -${_rc}|" Makefile

  echo "Setting version..."
  echo "-$pkgrel" > localversion.10-pkgrel

  # add upstream patch
  if [[ -z "$_rc" ]] && [[ -e "../patch-${pkgver}" ]]; then
    msg "add upstream patch"
    patch -p1 -i "../patch-${pkgver}"
  fi

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    src="${src%.zst}"
    [[ $src = *.patch ]] || continue
    echo "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  echo "Setting config..."
  cp ../config .config
  make olddefconfig
  diff -u ../config .config || :

  make -s kernelrelease > version
  msg "Prepared $pkgbase version $(<version)"
}

build() {
  cd $_srcdir
  make ${MAKEFLAGS} bzImage modules
  make -C tools/bpf/bpftool vmlinux.h feature-clang-bpf-co-re=1
}

_package() {
  pkgdesc="The Linux $_basekernel kernel and modules"
  depends=(
    'coreutils'
    'initramfs'
    'kmod'
  )
  optdepends=(
    'linux-firmware: firmware images needed for some devices'
    'scx-scheds: to use sched-ext schedulers'
    'wireless-regdb: to set the correct wireless channels of your country'
  )
  provides=(
    "linux=${pkgver}"
    KSMBD-MODULE
    VIRTUALBOX-GUEST-MODULES
    WIREGUARD-MODULE
  )
  replaces=(
    virtualbox-guest-modules
    wireguard
  )

  cd $_srcdir
  local modulesdir="$pkgdir/usr/lib/modules/$(<version)"

  echo "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "$pkgbase" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"
  echo "${_basekernel}-${CARCH}" | install -Dm644 /dev/stdin "$modulesdir/kernelbase"

  # add kernel version
  mkdir -p "${pkgdir}/boot"
  echo "$(<version) x64" > "${pkgdir}/boot/${pkgbase}-${CARCH}.kver"

  echo "Installing modules..."
  ZSTD_CLEVEL=19 make INSTALL_MOD_PATH="$pkgdir/usr" INSTALL_MOD_STRIP=1 \
    DEPMOD=/doesnt/exist modules_install  # Suppress depmod

  # remove build link
  rm "$modulesdir"/build

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "$(<version)"
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the Linux $_basekernel kernel"
  depends=(pahole)
  provides=("linux-headers=$pkgver")

  cd $_srcdir
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  echo "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux tools/bpf/bpftool/vmlinux.h
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts
  ln -srt "$builddir" "$builddir/scripts/gdb/vmlinux-gdb.py"

  # required when STACK_VALIDATION is enabled
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # required when DEBUG_INFO_BTF_MODULES is enabled
  install -Dt "$builddir/tools/bpf/resolve_btfids" tools/bpf/resolve_btfids/resolve_btfids

  echo "Installing headers..."
  cp -t "$builddir" -a include
  cp -t "$builddir/arch/x86" -a arch/x86/include
  install -Dt "$builddir/arch/x86/kernel" -m644 arch/x86/kernel/asm-offsets.s

  install -Dt "$builddir/drivers/md" -m644 drivers/md/*.h
  install -Dt "$builddir/net/mac80211" -m644 net/mac80211/*.h

  # https://bugs.archlinux.org/task/13146
  install -Dt "$builddir/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # https://bugs.archlinux.org/task/20402
  install -Dt "$builddir/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "$builddir/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "$builddir/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # https://bugs.archlinux.org/task/71392
  install -Dt "$builddir/drivers/iio/common/hid-sensors" -m644 drivers/iio/common/hid-sensors/*.h

  echo "Installing KConfig files..."
  find . -name 'Kconfig*' -exec install -Dm644 {} "$builddir/{}" \;

  echo "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */x86/ ]] && continue
    echo "Removing $(basename "$arch")"
    rm -r "$arch"
  done

  echo "Removing documentation..."
  rm -r "$builddir/Documentation"

  echo "Removing broken symlinks..."
  find -L "$builddir" -type l -printf 'Removing %P\n' -delete

  echo "Removing loose objects..."
  find "$builddir" -type f -name '*.o' -printf 'Removing %P\n' -delete

  echo "Stripping build tools..."
  local file
  while read -rd '' file; do
    case "$(file -Sib "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip -v $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip -v $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip -v $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip -v $STRIP_SHARED "$file" ;;
    esac
  done < <(find "$builddir" -type f -perm -u+x ! -name vmlinux -print0)

  echo "Stripping vmlinux..."
  strip -v $STRIP_STATIC "$builddir/vmlinux"

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"
}

pkgname=(
  "$pkgbase"
  "$pkgbase-headers"
)
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#$pkgbase}")
    _package${_p#$pkgbase}
  }"
done
