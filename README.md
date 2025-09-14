# Rick and Morty Episodes Explorer 🛸

A modern, responsive Vue.js application that displays episodes from the Rick and Morty TV series using the [Rick and Morty API](https://rickandmortyapi.com/). Built with Vue 3, Vite, and styled with DaisyUI + Tailwind CSS for a beautiful, interactive user experience.

## ✨ Features

- **Episode Grid Display**: Browse all Rick and Morty episodes in a responsive card layout
- **Character Avatars**: View character avatars for each episode with overflow indicators
- **Episode Details Modal**: Click on any episode card to view detailed information
- **Pagination**: Navigate through multiple pages of episodes
- **Responsive Design**: Optimized for desktop, tablet, and mobile devices
- **Modern UI**: Clean, accessible interface using DaisyUI components
- **Loading States**: Smooth loading indicators for better UX

## 🚀 Tech Stack

- **Frontend Framework**: Vue 3 (Composition API)
- **Build Tool**: Vite
- **Styling**: Tailwind CSS + DaisyUI
- **HTTP Client**: Axios
- **Routing**: Vue Router
- **Auto Imports**: Unplugin Auto Import & Components
- **Code Quality**: ESLint + Prettier

## 📦 Project Structure

```
src/
├── components/
│   ├── BadgeAirDate.vue      # Air date badge component
│   ├── BadgeEpisode.vue      # Episode number badge component
│   ├── CardBase.vue          # Episode card component
│   └── ModalEpisode.vue      # Episode details modal
├── layouts/
│   └── LayoutDefault.vue     # Default layout wrapper
├── pages/
│   └── HomeView.vue          # Main episodes listing page
├── assets/
│   └── main.css              # Global styles
└── App.vue                   # Root component
```

## 🛠️ Installation & Setup

### Prerequisites

- Node.js (^20.19.0 || >=22.12.0)
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd mvp-daisyui
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

## 📜 Available Scripts

- **`npm run dev`** - Start development server with hot reload
- **`npm run build`** - Build for production
- **`npm run preview`** - Preview production build locally
- **`npm run lint`** - Run ESLint to check code quality
- **`npm run format`** - Format code with Prettier

## 🎯 Usage

1. **Browse Episodes**: The home page displays a grid of episode cards showing episode names, numbers, air dates, and character avatars
2. **View Details**: Click on any episode card to open a modal with detailed information
3. **Navigate Pages**: Use the pagination buttons at the bottom to browse through all episodes
4. **Character Avatars**: Each card shows up to 5 character avatars with a counter for additional characters

## 🔧 Configuration

### Vite Configuration
The project uses several Vite plugins for enhanced development experience:
- Vue 3 support with devtools
- Tailwind CSS integration
- Auto-import for Vue composables
- Auto-import for components

### ESLint & Prettier
Code quality is maintained with ESLint and Prettier configurations for consistent code style.

## 🌐 API Integration

This application consumes the [Rick and Morty API](https://rickandmortyapi.com/) endpoints:
- `/api/episode` - Fetch episodes with pagination
- `/api/episode/{id}` - Fetch specific episode details
- `/api/character/avatar/{id}.jpeg` - Character avatar images

## 🎨 UI Components

The application uses DaisyUI components for consistent styling:
- **Cards**: Episode display containers
- **Badges**: Episode numbers and air dates
- **Modals**: Episode detail overlays
- **Buttons**: Pagination and interactions
- **Avatars**: Character images with grouping
- **Loading**: Spinner indicators

## 📱 Responsive Design

The layout adapts to different screen sizes:
- **Mobile**: Single column grid
- **Tablet**: Two column grid
- **Desktop**: Three column grid

## 🔄 Recent Bug Fixes

- Fixed reactivity issue in `CardBase.vue` where `splice()` was incorrectly used instead of `slice()`
- Improved modal loading states and data reset functionality
- Enhanced character avatar display with proper overflow handling

## 🚀 Deployment

To build for production:

```bash
npm run build
```

The built files will be in the `dist/` directory, ready for deployment to any static hosting service.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- [Rick and Morty API](https://rickandmortyapi.com/) for providing the data
- [DaisyUI](https://daisyui.com/) for the beautiful UI components
- [Tailwind CSS](https://tailwindcss.com/) for the utility-first CSS framework
