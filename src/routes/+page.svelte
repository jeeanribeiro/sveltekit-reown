<script>
    import { createAppKit } from '@reown/appkit'
    import { mainnet, arbitrum } from '@reown/appkit/networks'
    import { WagmiAdapter } from '@reown/appkit-adapter-wagmi'

    // 1. Get a project ID at https://cloud.reown.com
    const projectId = '472ff84cf82711483c07cdc9dfa4c92d'

    export const networks = [mainnet, arbitrum]

    // 2. Set up Wagmi adapter
    const wagmiAdapter = new WagmiAdapter({
        projectId,
        networks
    })

    // 3. Configure the metadata
    const metadata = {
        name: 'AppKit',
        description: 'AppKit Example',
        url: 'https://example.com', // origin must match your domain & subdomain
        icons: ['https://avatars.githubusercontent.com/u/179229932']
    }

    // 3. Create the modal
    const modal = createAppKit({
        adapters: [wagmiAdapter],
        networks: [mainnet, arbitrum],
        metadata,
        projectId,
        features: {
            analytics: true // Optional - defaults to your Cloud configuration
        }
    })
</script>

<div id="app">
    <button id="open-connect-modal" onclick={() => modal.open()}>Open Modal</button>
    <button id="open-network-modal" onclick={() => modal.open({ view: 'Networks' })}>Open Networks</button>
</div>
