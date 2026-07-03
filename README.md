{
  "name": "spotify-clone",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "next": "^14.0.0",
    "zustand": "^4.4.0",
    "lucide-react": "^0.294.0"
  },
  "devDependencies": {
    "typescript": "^5.2.0",
    "@types/node": "^20.4.0",
    "@types/react": "^18.2.0",
    "@types/react-dom": "^18.2.0",
    "autoprefixer": "^10.4.14",
    "postcss": "^8.4.27",
    "tailwindcss": "^3.3.0",
    "eslint": "^8.45.0",
    "eslint-config-next": "^14.0.0"
  }
}
{
  "compilerOptions": {
    "target": "es2020",
    "useDefineForClassFields": true,
    "lib": ["es2020", "dom", "dom.iterable"],
    "module": "esnext",
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,

    /* Bundler mode */
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",

    /* Linting */
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["src"],
  "references": [{ "path": "./tsconfig.node.json" }]
}
import type { Config } from 'tailwindcss'

const config: Config = {
  content: [
    './src/pages/**/*.{js,ts,jsx,tsx,mdx}',
    './src/components/**/*.{js,ts,jsx,tsx,mdx}',
    './src/app/**/*.{js,ts,jsx,tsx,mdx}',
    './app/**/*.{js,ts,jsx,tsx,mdx}',
    './components/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      colors: {
        spotify: {
          bg: '#121212',
          card: '#181818',
          hover: '#282828',
          green: '#1DB954',
          text: '#FFFFFF',
          'text-secondary': '#B3B3B3',
        },
      },
      backgroundColor: {
        primary: '#121212',
        secondary: '#181818',
      },
    },
  },
  plugins: [],
}
export default config
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  images: {
    unoptimized: true,
  },
}

export default nextConfig
# dependencies
/node_modules
/.pnp
.pnp.js

# testing
/coverage

# next.js
/.next/
/out/

# production
/build

# misc
.DS_Store
*.pem

# debug
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# local env files
.env*.local

# vercel
.vercel

# typescript
*.tsbuildinfo
next-env.d.ts
# dependencies
/node_modules
/.pnp
.pnp.js

# testing
/coverage

# next.js
/.next/
/out/

# production
/build

# misc
.DS_Store
*.pem

# debug
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# local env files
.env*.local

# vercel
.vercel

# typescript
*.tsbuildinfo
next-env.d.ts
@tailwind base;
@tailwind components;
@tailwind utilities;

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #121212;
  color: #ffffff;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
}

/* Scrollbar styling */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #121212;
}

::-webkit-scrollbar-thumb {
  background: #404040;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #535353;
}

/* Smooth transitions */
button,
a {
  transition: all 0.2s ease-in-out;
}

/* Hide audio player default controls */
audio {
  display: none;
}
export interface Track {
  id: string;
  title: string;
  artist: string;
  album: string;
  duration: number; // in seconds
  coverUrl: string;
  audioUrl: string;
  plays: number;
}

export interface Playlist {
  id: string;
  name: string;
  description: string;
  coverUrl: string;
  tracks: Track[];
  createdAt: string;
}

export interface Artist {
  id: string;
  name: string;
  image: string;
  followers: number;
}

export interface Album {
  id: string;
  title: string;
  artist: string;
  coverUrl: string;
  tracks: Track[];
  releaseDate: string;
}
import { Track, Playlist, Artist, Album } from './types';

const mockTracks: Track[] = [
  {
    id: '1',
    title: 'Blinding Lights',
    artist: 'The Weeknd',
    album: 'After Hours',
    duration: 200,
    coverUrl: 'https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=300&h=300&fit=crop',
    audioUrl: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3',
    plays: 2500000,
  },
  {
    id: '2',
    title: 'Shape of You',
    artist: 'Ed Sheeran',
    album: '÷',
    duration: 235,
    coverUrl: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?w=300&h=300&fit=crop',
    audioUrl: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3',
    plays: 3000000,
  },
  {
    id: '3',
    title: 'Levitating',
    artist: 'Dua Lipa',
    album: 'Future Nostalgia',
    duration: 203,
    coverUrl: 'https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?w=300&h=300&fit=crop',
    audioUrl: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3',
    plays: 2800000,
  },
  {
    id: '4',
    title: 'Heat Waves',
    artist: 'Glass Animals',
    album: 'Dreamland',
    duration: 239,
    coverUrl: 'https://images.unsplash.com/photo-1459749411175-04bf5292ceea?w=300&h=300&fit=crop',
    audioUrl: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-4.mp3',
    plays: 2200000,
  },
  {
    id: '5',
    title: 'Anti-Hero',
    artist: 'Taylor Swift',
    album: 'Midnights',
    duration: 200,
    coverUrl: 'https://images.unsplash.com/photo-1484704849700-f032a568e944?w=300&h=300&fit=crop',
    audioUrl: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-5.mp3',
    plays: 1800000,
  },
  {
    id: '6',
    title: 'Tes Larmes',
    artist: 'Stromae',
    album: 'Racine Carrée',
    duration: 185,
    coverUrl: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?w=300&h=300&fit=crop',
    audioUrl: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-6.mp3',
    plays: 1500000,
  },
];

const mockPlaylists: Playlist[] = [
  {
    id: 'pl1',
    name: 'Today\'s Top Hits',
    description: 'The hottest tracks right now',
    coverUrl: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?w=300&h=300&fit=crop',
    tracks: [mockTracks[0], mockTracks[1], mockTracks[2]],
    createdAt: '2024-01-15',
  },
  {
    id: 'pl2',
    name: 'Chill Vibes',
    description: 'Relaxing music for every moment',
    coverUrl: 'https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=300&h=300&fit=crop',
    tracks: [mockTracks[3], mockTracks[4], mockTracks[5]],
    createdAt: '2024-01-10',
  },
  {
    id: 'pl3',
    name: 'Workout Mix',
    description: 'High energy tracks to pump you up',
    coverUrl: 'https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?w=300&h=300&fit=crop',
    tracks: [mockTracks[0], mockTracks[2], mockTracks[4]],
    createdAt: '2024-01-05',
  },
  {
    id: 'pl4',
    name: 'Late Night Drives',
    description: 'Perfect soundtrack for night drives',
    coverUrl: 'https://images.unsplash.com/photo-1459749411175-04bf5292ceea?w=300&h=300&fit=crop',
    tracks: [mockTracks[1], mockTracks[3], mockTracks[5]],
    createdAt: '2023-12-28',
  },
];

const mockArtists: Artist[] = [
  {
    id: 'ar1',
    name: 'The Weeknd',
    image: 'https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=300&h=300&fit=crop',
    followers: 75000000,
  },
  {
    id: 'ar2',
    name: 'Ed Sheeran',
    image: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?w=300&h=300&fit=crop',
    followers: 85000000,
  },
  {
    id: 'ar3',
    name: 'Dua Lipa',
    image: 'https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?w=300&h=300&fit=crop',
    followers: 65000000,
  },
  {
    id: 'ar4',
    name: 'Taylor Swift',
    image: 'https://images.unsplash.com/photo-1484704849700-f032a568e944?w=300&h=300&fit=crop',
    followers: 95000000,
  },
];

const mockAlbums: Album[] = [
  {
    id: 'alb1',
    title: 'After Hours',
    artist: 'The Weeknd',
    coverUrl: 'https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=300&h=300&fit=crop',
    tracks: [mockTracks[0], mockTracks[1]],
    releaseDate: '2020-03-20',
  },
  {
    id: 'alb2',
    title: '÷',
    artist: 'Ed Sheeran',
    coverUrl: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?w=300&h=300&fit=crop',
    tracks: [mockTracks[1], mockTracks[3]],
    releaseDate: '2017-03-03',
  },
  {
    id: 'alb3',
    title: 'Midnights',
    artist: 'Taylor Swift',
    coverUrl: 'https://images.unsplash.com/photo-1484704849700-f032a568e944?w=300&h=300&fit=crop',
    tracks: [mockTracks[4], mockTracks[5]],
    releaseDate: '2022-10-21',
  },
];

export { mockTracks, mockPlaylists, mockArtists, mockAlbums };
import { create } from 'zustand';
import { Track, Playlist } from '@/lib/types';

interface MusicStore {
  // Player state
  currentTrack: Track | null;
  isPlaying: boolean;
  isShuffle: boolean;
  repeatMode: 'off' | 'all' | 'one';
  volume: number;
  currentTime: number;
  duration: number;
  queue: Track[];
  queueIndex: number;

  // Playlist state
  playlists: Playlist[];
  likedTracks: Track[];

  // Actions
  setCurrentTrack: (track: Track | null) => void;
  setIsPlaying: (playing: boolean) => void;
  setShuffle: (shuffle: boolean) => void;
  setRepeatMode: (mode: 'off' | 'all' | 'one') => void;
  setVolume: (volume: number) => void;
  setCurrentTime: (time: number) => void;
  setDuration: (duration: number) => void;
  setQueue: (queue: Track[]) => void;
  setQueueIndex: (index: number) => void;

  playTrack: (track: Track) => void;
  pauseTrack: () => void;
  playNext: () => void;
  playPrevious: () => void;

  createPlaylist: (name: string, description: string) => void;
  deletePlaylist: (id: string) => void;
  addTrackToPlaylist: (playlistId: string, track: Track) => void;
  removeTrackFromPlaylist: (playlistId: string, trackId: string) => void;

  likeTrack: (track: Track) => void;
  unlikeTrack: (trackId: string) => void;
  isTrackLiked: (trackId: string) => boolean;
}

const useMusicStore = create<MusicStore>((set, get) => ({
  // Initial state
  currentTrack: null,
  isPlaying: false,
  isShuffle: false,
  repeatMode: 'off',
  volume: 0.7,
  currentTime: 0,
  duration: 0,
  queue: [],
  queueIndex: 0,
  playlists: [],
  likedTracks: [],

  // Setters
  setCurrentTrack: (track) => set({ currentTrack: track }),
  setIsPlaying: (playing) => set({ isPlaying: playing }),
  setShuffle: (shuffle) => set({ isShuffle: shuffle }),
  setRepeatMode: (mode) => set({ repeatMode: mode }),
  setVolume: (volume) => set({ volume: Math.max(0, Math.min(1, volume)) }),
  setCurrentTime: (time) => set({ currentTime: time }),
  setDuration: (duration) => set({ duration }),
  setQueue: (queue) => set({ queue }),
  setQueueIndex: (index) => set({ queueIndex: index }),

  // Player actions
  playTrack: (track) => {
    set({
      currentTrack: track,
      isPlaying: true,
      queue: [track],
      queueIndex: 0,
      currentTime: 0,
    });
  },

  pauseTrack: () => set({ isPlaying: false }),

  playNext: () => {
    const { queue, queueIndex, isShuffle, repeatMode } = get();
    if (queue.length === 0) return;

    let nextIndex = queueIndex + 1;

    if (isShuffle) {
      nextIndex = Math.floor(Math.random() * queue.length);
    } else if (nextIndex >= queue.length) {
      if (repeatMode === 'all') {
        nextIndex = 0;
      } else {
        set({ isPlaying: false });
        return;
      }
    }

    set({
      currentTrack: queue[nextIndex],
      queueIndex: nextIndex,
      currentTime: 0,
    });
  },

  playPrevious: () => {
    const { queue, queueIndex, currentTime } = get();
    if (queue.length === 0) return;

    if (currentTime > 3) {
      set({ currentTime: 0 });
    } else {
      const prevIndex = queueIndex - 1;
      if (prevIndex >= 0) {
        set({
          currentTrack: queue[prevIndex],
          queueIndex: prevIndex,
          currentTime: 0,
        });
      }
    }
  },

  // Playlist actions
  createPlaylist: (name, description) => {
    const playlist: Playlist = {
      id: `pl-${Date.now()}`,
      name,
      description,
      coverUrl: 'https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f?w=300&h=300&fit=crop',
      tracks: [],
      createdAt: new Date().toISOString(),
    };
    set((state) => ({
      playlists: [...state.playlists, playlist],
    }));
  },

  deletePlaylist: (id) => {
    set((state) => ({
      playlists: state.playlists.filter((p) => p.id !== id),
    }));
  },

  addTrackToPlaylist: (playlistId, track) => {
    set((state) => ({
      playlists: state.playlists.map((p) =>
        p.id === playlistId
          ? { ...p, tracks: [...p.tracks, track] }
          : p
      ),
    }));
  },

  removeTrackFromPlaylist: (playlistId, trackId) => {
    set((state) => ({
      playlists: state.playlists.map((p) =>
        p.id === playlistId
          ? { ...p, tracks: p.tracks.filter((t) => t.id !== trackId) }
          : p
      ),
    }));
  },

  // Like/Unlike actions
  likeTrack: (track) => {
    set((state) => ({
      likedTracks: state.likedTracks.some((t) => t.id === track.id)
        ? state.likedTracks
        : [...state.likedTracks, track],
    }));
  },

  unlikeTrack: (trackId) => {
    set((state) => ({
      likedTracks: state.likedTracks.filter((t) => t.id !== trackId),
    }));
  },

  isTrackLiked: (trackId) => {
    const { likedTracks } = get();
    return likedTracks.some((t) => t.id === trackId);
  },
}));

export default useMusicStore;
'use client';

import Link from 'next/link';
import { Home, Search, Library, Plus, Heart } from 'lucide-react';
import useMusicStore from '@/store/musicStore';
import { useState } from 'react';

const Sidebar = () => {
  const { playlists, createPlaylist } = useMusicStore();
  const [showPlaylistForm, setShowPlaylistForm] = useState(false);
  const [playlistName, setPlaylistName] = useState('');

  const handleCreatePlaylist = (e: React.FormEvent) => {
    e.preventDefault();
    if (playlistName.trim()) {
      createPlaylist(playlistName, 'New playlist');
      setPlaylistName('');
      setShowPlaylistForm(false);
    }
  };

  return (
    <aside className="hidden md:flex flex-col w-64 bg-spotify-bg border-r border-spotify-hover h-screen overflow-y-auto fixed left-0 top-0 z-40">
      {/* Logo */}
      <div className="p-6 pb-4 border-b border-spotify-hover">
        <h1 className="text-2xl font-bold text-spotify-green flex items-center gap-2">
          🎵 Spotify
        </h1>
      </div>

      {/* Main Navigation */}
      <nav className="flex-1 px-4 py-6 space-y-6">
        {/* Home */}
        <Link
          href="/"
          className="flex items-center gap-4 px-4 py-3 rounded-lg hover:bg-spotify-hover transition-colors text-spotify-text-secondary hover:text-spotify-text"
        >
          <Home size={24} />
          <span className="text-base font-medium">Home</span>
        </Link>

        {/* Search */}
        <Link
          href="/search"
          className="flex items-center gap-4 px-4 py-3 rounded-lg hover:bg-spotify-hover transition-colors text-spotify-text-secondary hover:text-spotify-text"
        >
          <Search size={24} />
          <span className="text-base font-medium">Search</span>
        </Link>

        {/* Library */}
        <Link
          href="/library"
          className="flex items-center gap-4 px-4 py-3 rounded-lg hover:bg-spotify-hover transition-colors text-spotify-text-secondary hover:text-spotify-text"
        >
          <Library size={24} />
          <span className="text-base font-medium">Your Library</span>
        </Link>

        {/* Liked Songs */}
        <Link
          href="/liked"
          className="flex items-center gap-4 px-4 py-3 rounded-lg hover:bg-spotify-hover transition-colors text-spotify-text-secondary hover:text-spotify-text"
        >
          <Heart size={24} />
          <span className="text-base font-medium">Liked Songs</span>
        </Link>
      </nav>

      {/* Playlists Section */}
      <div className="px-4 py-6 border-t border-spotify-hover flex-1 overflow-y-auto">
        <div className="flex items-center justify-between mb-4">
          <h2 className="text-sm font-bold text-spotify-text-secondary uppercase tracking-wide">
            Playlists
          </h2>
          <button
            onClick={() => setShowPlaylistForm(!showPlaylistForm)}
            className="p-1 hover:bg-spotify-hover rounded-full transition-colors"
            title="Create playlist"
          >
            <Plus size={18} className="text-spotify-green" />
          </button>
        </div>

        {/* Create Playlist Form */}
        {showPlaylistForm && (
          <form onSubmit={handleCreatePlaylist} className="mb-4">
            <input
              type="text"
              placeholder="Playlist name"
              value={playlistName}
              onChange={(e) => setPlaylistName(e.target.value)}
              className="w-full px-3 py-2 bg-spotify-card text-sm rounded border border-spotify-hover text-white placeholder-spotify-text-secondary focus:outline-none focus:border-spotify-green"
              autoFocus
            />
            <div className="flex gap-2 mt-2">
              <button
                type="submit"
                className="flex-1 px-3 py-1 bg-spotify-green text-black text-sm font-bold rounded hover:bg-opacity-90 transition-opacity"
              >
                Create
              </button>
              <button
                type="button"
                onClick={() => setShowPlaylistForm(false)}
                className="flex-1 px-3 py-1 bg-spotify-hover text-white text-sm rounded hover:bg-opacity-70 transition-opacity"
              >
                Cancel
              </button>
            </div>
          </form>
        )}

        {/* Playlist List */}
        <div className="space-y-2">
          {playlists.map((playlist) => (
            <Link
              key={playlist.id}
              href={`/playlist/${playlist.id}`}
              className="block px-3 py-2 text-sm text-spotify-text-secondary hover:text-spotify-text rounded hover:bg-spotify-hover transition-colors truncate"
              title={playlist.name}
            >
              {playlist.name}
            </Link>
          ))}
        </div>
      </div>
    </aside>
  );
};

export default Sidebar;
'use client';

import { Search, ChevronLeft, ChevronRight, User } from 'lucide-react';
import { useRouter } from 'next/navigation';
import { useState } from 'react';
import Link from 'next/link';

const TopBar = () => {
  const router = useRouter();
  const [searchQuery, setSearchQuery] = useState('');

  const handleSearch = (e: React.FormEvent) => {
    e.preventDefault();
    if (searchQuery.trim()) {
      router.push(`/search?q=${encodeURIComponent(searchQuery)}`);
    }
  };

  return (
    <header className="fixed top-0 left-0 right-0 z-30 bg-gradient-to-b from-spotify-card to-transparent md:left-64 h-20 border-b border-spotify-hover">
      <div className="flex items-center justify-between h-full px-4 md:px-6">
        {/* Left: Navigation arrows */}
        <div className="flex items-center gap-2">
          <button
            onClick={() => router.back()}
            className="p-2 hover:bg-spotify-hover rounded-full transition-colors"
            aria-label="Go back"
          >
            <ChevronLeft size={24} className="text-spotify-text-secondary" />
          </button>
          <button
            onClick={() => router.forward()}
            className="p-2 hover:bg-spotify-hover rounded-full transition-colors"
            aria-label="Go forward"
          >
            <ChevronRight size={24} className="text-spotify-text-secondary" />
          </button>
        </div>

        {/* Center: Search */}
        <form onSubmit={handleSearch} className="flex-1 max-w-md mx-4">
          <div className="relative">
            <Search size={18} className="absolute left-3 top-1/2 transform -translate-y-1/2 text-spotify-text-secondary" />
            <input
              type="text"
              placeholder="Search songs, artists, albums..."
              value={searchQuery}
              onChange={(e) => setSearchQuery(e.target.value)}
              className="w-full pl-10 pr-4 py-2 bg-spotify-card text-white text-sm rounded-full placeholder-spotify-text-secondary focus:outline-none focus:ring-2 focus:ring-spotify-green"
            />
          </div>
        </form>

        {/* Right: Profile */}
        <Link
          href="/profile"
          className="flex items-center gap-2 px-4 py-2 bg-spotify-card rounded-full hover:bg-spotify-hover transition-colors"
        >
          <div className="w-8 h-8 bg-spotify-green rounded-full flex items-center justify-center">
            <User size={18} className="text-black" />
          </div>
          <span className="text-sm font-medium hidden sm:inline">Profile</span>
        </Link>
      </div>
    </header>
  );
};

export default TopBar;
'use client';

import useMusicStore from '@/store/musicStore';
import {
  Play,
  Pause,
  SkipBack,
  SkipForward,
  Shuffle,
  Repeat,
  Volume2,
  Heart,
} from 'lucide-react';
import { useEffect, useRef } from 'react';
import Image from 'next/image';

const Player = () => {
  const {
    currentTrack,
    isPlaying,
    isShuffle,
    repeatMode,
    volume,
    currentTime,
    duration,
    playTrack,
    pauseTrack,
    playNext,
    playPrevious,
    setShuffle,
    setRepeatMode,
    setVolume,
    setCurrentTime,
    setDuration,
    likeTrack,
    unlikeTrack,
    isTrackLiked,
  } = useMusicStore();

  const audioRef = useRef<HTMLAudioElement>(null);

  // Sync audio element with store
  useEffect(() => {
    if (!audioRef.current) return;

    if (isPlaying && currentTrack) {
      audioRef.current.src = currentTrack.audioUrl;
      audioRef.current.play().catch(() => {
        // Autoplay policy might prevent this
      });
    } else {
      audioRef.current.pause();
    }
  }, [isPlaying, currentTrack]);

  // Handle audio events
  useEffect(() => {
    const audio = audioRef.current;
    if (!audio) return;

    const handleTimeUpdate = () => {
      setCurrentTime(audio.currentTime);
    };

    const handleLoadedMetadata = () => {
      setDuration(audio.duration);
    };

    const handleEnded = () => {
      playNext();
    };

    audio.addEventListener('timeupdate', handleTimeUpdate);
    audio.addEventListener('loadedmetadata', handleLoadedMetadata);
    audio.addEventListener('ended', handleEnded);

    return () => {
      audio.removeEventListener('timeupdate', handleTimeUpdate);
      audio.removeEventListener('loadedmetadata', handleLoadedMetadata);
      audio.removeEventListener('ended', handleEnded);
    };
  }, [setCurrentTime, setDuration, playNext]);

  // Handle volume
  useEffect(() => {
    if (audioRef.current) {
      audioRef.current.volume = volume;
    }
  }, [volume]);

  const formatTime = (time: number) => {
    if (!time || isNaN(time)) return '0:00';
    const minutes = Math.floor(time / 60);
    const seconds = Math.floor(time % 60);
    return `${minutes}:${seconds.toString().padStart(2, '0')}`;
  };

  const handleProgressClick = (e: React.MouseEvent<HTMLDivElement>) => {
    if (!audioRef.current) return;
    const rect = e.currentTarget.getBoundingClientRect();
    const percent = (e.clientX - rect.left) / rect.width;
    audioRef.current.currentTime = percent * duration;
  };

  const toggleLike = () => {
    if (!currentTrack) return;
    if (isTrackLiked(currentTrack.id)) {
      unlikeTrack(currentTrack.id);
    } else {
      likeTrack(currentTrack);
    }
  };

  return (
    <>
      <audio ref={audioRef} />
      <div className="fixed bottom-0 left-0 right-0 bg-spotify-card border-t border-spotify-hover px-4 py-4 z-50">
        {/* Main Player Container */}
        <div className="max-w-7xl mx-auto">
          {/* Progress Bar */}
          <div className="mb-4 space-y-2">
            <div
              onClick={handleProgressClick}
              className="w-full h-1 bg-spotify-hover rounded-full cursor-pointer group hover:h-2 transition-all"
            >
              <div
                className="h-full bg-spotify-green rounded-full"
                style={{ width: duration ? `${(currentTime / duration) * 100}%` : '0%' }}
              />
            </div>
            <div className="flex justify-between text-xs text-spotify-text-secondary">
              <span>{formatTime(currentTime)}</span>
              <span>{formatTime(duration)}</span>
            </div>
          </div>

          {/* Player Controls */}
          <div className="flex items-center justify-between gap-4">
            {/* Left: Track Info */}
            <div className="flex items-center gap-3 min-w-0 w-full md:w-auto">
              {currentTrack ? (
                <>
                  <div className="w-14 h-14 flex-shrink-0 rounded overflow-hidden bg-spotify-hover">
                    <Image
                      src={currentTrack.coverUrl}
                      alt={currentTrack.title}
                      width={56}
                      height={56}
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <div className="flex-1 min-w-0">
                    <p className="text-sm font-semibold text-white truncate">{currentTrack.title}</p>
                    <p className="text-xs text-spotify-text-secondary truncate">{currentTrack.artist}</p>
                  </div>
                </>
              ) : (
                <div className="text-sm text-spotify-text-secondary">No track playing</div>
              )}
            </div>

            {/* Center: Controls */}
            <div className="hidden md:flex items-center justify-center gap-4">
              <button
                onClick={() => setShuffle(!isShuffle)}
                className={`p-2 rounded-full transition-colors ${
                  isShuffle ? 'text-spotify-green' : 'text-spotify-text-secondary hover:text-spotify-text'
                }`}
              >
                <Shuffle size={20} />
              </button>
              <button
                onClick={playPrevious}
                className="p-2 text-spotify-text-secondary hover:text-spotify-text rounded-full transition-colors"
              >
                <SkipBack size={20} />
              </button>
              <button
                onClick={() => (isPlaying ? pauseTrack() : currentTrack && playTrack(currentTrack))}
                className="w-10 h-10 bg-spotify-green text-black rounded-full flex items-center justify-center hover:scale-105 transition-transform"
              >
                {isPlaying ? <Pause size={20} fill="black" /> : <Play size={20} fill="black" />}
              </button>
              <button
                onClick={playNext}
                className="p-2 text-spotify-text-secondary hover:text-spotify-text rounded-full transition-colors"
              >
                <SkipForward size={20} />
              </button>
              <button
                onClick={() => {
                  const modes: Array<'off' | 'all' | 'one'> = ['off', 'all', 'one'];
                  const currentIndex = modes.indexOf(repeatMode);
                  setRepeatMode(modes[(currentIndex + 1) % modes.length]);
                }}
                className={`p-2 rounded-full transition-colors ${
                  repeatMode !== 'off' ? 'text-spotify-green' : 'text-spotify-text-secondary hover:text-spotify-text'
                }`}
              >
                <Repeat size={20} />
                {repeatMode === 'one' && <span className="text-xs ml-1">1</span>}
              </button>
            </div>

            {/* Right: Volume & Like */}
            <div className="hidden md:flex items-center gap-4">
              <button
                onClick={toggleLike}
                className={`p-2 rounded-full transition-colors ${
                  currentTrack && isTrackLiked(currentTrack.id)
                    ? 'text-spotify-green'
                    : 'text-spotify-text-secondary hover:text-spotify-text'
                }`}
              >
                <Heart size={20} fill={currentTrack && isTrackLiked(currentTrack.id) ? 'currentColor' : 'none'} />
              </button>
              <div className="flex items-center gap-2">
                <Volume2 size={18} className="text-spotify-text-secondary" />
                <input
                  type="range"
                  min="0"
                  max="1"
                  step="0.01"
                  value={volume}
                  onChange={(e) => setVolume(parseFloat(e.target.value))}
                  className="w-24 h-1 bg-spotify-hover rounded-full appearance-none cursor-pointer"
                  style={{
                    background: `linear-gradient(to right, #1DB954 0%, #1DB954 ${volume * 100}%, #404040 ${volume * 100}%, #404040 100%)`,
                  }}
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </>
  );
};

export default Player;
'use client';

import Image from 'next/image';
import Link from 'next/link';
import { Play } from 'lucide-react';
import useMusicStore from '@/store/musicStore';
import { Playlist } from '@/lib/types';

interface PlaylistCardProps {
  playlist: Playlist;
}

const PlaylistCard = ({ playlist }: PlaylistCardProps) => {
  const { playTrack } = useMusicStore();

  const handlePlayClick = () => {
    if (playlist.tracks.length > 0) {
      playTrack(playlist.tracks[0]);
    }
  };

  return (
    <Link href={`/playlist/${playlist.id}`}>
      <div className="group bg-spotify-card rounded-lg p-4 hover:bg-spotify-hover transition-all hover:scale-105 cursor-pointer">
        <div className="relative mb-4 overflow-hidden rounded">
          <Image
            src={playlist.coverUrl}
            alt={playlist.name}
            width={200}
            height={200}
            className="w-full aspect-square object-cover"
          />
          <button
            onClick={(e) => {
              e.preventDefault();
              handlePlayClick();
            }}
            className="absolute bottom-2 right-2 w-12 h-12 bg-spotify-green text-black rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transform translate-y-2 group-hover:translate-y-0 transition-all"
          >
            <Play size={24} fill="black" />
          </button>
        </div>
        <h3 className="font-semibold text-white truncate group-hover:text-spotify-green transition-colors">
          {playlist.name}
        </h3>
        <p className="text-xs text-spotify-text-secondary truncate">
          {playlist.tracks.length} songs
        </p>
      </div>
    </Link>
  );
};

export default PlaylistCard;
'use client';

import { Track } from '@/lib/types';
import useMusicStore from '@/store/musicStore';
import { Heart, MoreVertical } from 'lucide-react';
import { useState } from 'react';

interface TrackListProps {
  tracks: Track[];
  showPlaylistOptions?: boolean;
  playlistId?: string;
}

const TrackList = ({ tracks, showPlaylistOptions, playlistId }: TrackListProps) => {
  const { playTrack, currentTrack, likeTrack, unlikeTrack, isTrackLiked, removeTrackFromPlaylist } = useMusicStore();
  const [hoveredTrackId, setHoveredTrackId] = useState<string | null>(null);

  const handleRemoveFromPlaylist = (trackId: string) => {
    if (playlistId) {
      removeTrackFromPlaylist(playlistId, trackId);
    }
  };

  const toggleLike = (track: Track) => {
    if (isTrackLiked(track.id)) {
      unlikeTrack(track.id);
    } else {
      likeTrack(track);
    }
  };

  const formatTime = (seconds: number) => {
    const mins = Math.floor(seconds / 60);
    const secs = Math.floor(seconds % 60);
    return `${mins}:${secs.toString().padStart(2, '0')}`;
  };

  return (
    <div className="space-y-2">
      {tracks.map((track, index) => (
        <div
          key={track.id}
          onMouseEnter={() => setHoveredTrackId(track.id)}
          onMouseLeave={() => setHoveredTrackId(null)}
          onClick={() => playTrack(track)}
          className={`flex items-center gap-4 px-4 py-3 rounded-lg hover:bg-spotify-hover transition-colors cursor-pointer ${
            currentTrack?.id === track.id ? 'bg-spotify-hover' : ''
          }`}
        >
          {/* Track Number / Playing Indicator */}
          <div className="w-8 text-center text-sm text-spotify-text-secondary">
            {hoveredTrackId === track.id ? (
              <span className="text-spotify-green">▶</span>
            ) : (
              <span>{index + 1}</span>
            )}
          </div>

          {/* Track Info */}
          <div className="flex-1 min-w-0">
            <p className={`text-sm font-medium truncate ${
              currentTrack?.id === track.id ? 'text-spotify-green' : 'text-white'
            }`}>
              {track.title}
            </p>
            <p className="text-xs text-spotify-text-secondary truncate">{track.artist}</p>
          </div>

          {/* Album */}
          <div className="hidden md:block text-xs text-spotify-text-secondary truncate max-w-xs">
            {track.album}
          </div>

          {/* Duration / Actions */}
          <div className="flex items-center gap-3">
            {hoveredTrackId === track.id ? (
              <>
                <button
                  onClick={(e) => {
                    e.stopPropagation();
                    toggleLike(track);
                  }}
                  className="text-spotify-text-secondary hover:text-spotify-green transition-colors"
                >
                  <Heart
                    size={16}
                    fill={isTrackLiked(track.id) ? 'currentColor' : 'none'}
                    className={isTrackLiked(track.id) ? 'text-spotify-green' : ''}
                  />
                </button>
                {showPlaylistOptions && (
                  <button
                    onClick={(e) => {
                      e.stopPropagation();
                      handleRemoveFromPlaylist(track.id);
                    }}
                    className="text-spotify-text-secondary hover:text-red-500 transition-colors"
                  >
                    <MoreVertical size={16} />
                  </button>
                )}
              </>
            ) : null}
            <span className="text-xs text-spotify-text-secondary w-10 text-right">
              {formatTime(track.duration)}
            </span>
          </div>
        </div>
      ))}
    </div>
  );
};

export default TrackList;
import type { Metadata } from 'next';
import './globals.css';
import Sidebar from '@/components/Sidebar';
import TopBar from '@/components/TopBar';
import Player from '@/components/Player';

export const metadata: Metadata = {
  title: 'Spotify Clone',
  description: 'A modern music streaming web app inspired by Spotify',
};

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body className="bg-spotify-bg text-white">
        <Sidebar />
        <TopBar />
        <main className="md:ml-64 pt-24 pb-40 px-4 md:px-6">
          {children}
        </main>
        <Player />
      </body>
    </html>
  );
}
'use client';

import PlaylistCard from '@/components/PlaylistCard';
import { mockPlaylists, mockTracks } from '@/lib/mockData';
import useMusicStore from '@/store/musicStore';
import { useEffect } from 'react';

export default function Home() {
  const { setQueue } = useMusicStore();

  useEffect(() => {
    setQueue(mockTracks);
  }, [setQueue]);

  return (
    <div className="space-y-12">
      {/* Header */}
      <div>
        <h1 className="text-4xl md:text-5xl font-bold mb-2">Welcome back!</h1>
        <p className="text-spotify-text-secondary">Here's what you've been listening to lately</p>
      </div>

      {/* Featured Playlists */}
      <section>
        <h2 className="text-2xl font-bold mb-6">Featured Playlists</h2>
        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
          {mockPlaylists.map((playlist) => (
            <PlaylistCard key={playlist.id} playlist={playlist} />
          ))}
        </div>
      </section>

      {/* Popular Songs */}
      <section>
        <h2 className="text-2xl font-bold mb-6">Popular Right Now</h2>
        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
          {mockTracks.slice(0, 4).map((track) => (
            <div key={track.id} className="bg-spotify-card rounded-lg p-4 hover:bg-spotify-hover transition-all cursor-pointer group">
              <div className="relative mb-4 overflow-hidden rounded">
                <img
                  src={track.coverUrl}
                  alt={track.title}
                  className="w-full aspect-square object-cover group-hover:scale-105 transition-transform"
                />
              </div>
              <h3 className="font-semibold text-white truncate group-hover:text-spotify-green">
                {track.title}
              </h3>
              <p className="text-xs text-spotify-text-secondary truncate">{track.artist}</p>
            </div>
          ))}
        </div>
      </section>
    </div>
  );
}
'use client';

import { useState, useEffect } from 'react';
import { useSearchParams } from 'next/navigation';
import TrackList from '@/components/TrackList';
import PlaylistCard from '@/components/PlaylistCard';
import { mockTracks, mockPlaylists, mockArtists } from '@/lib/mockData';

export default function SearchPage() {
  const searchParams = useSearchParams();
  const query = searchParams.get('q')?.toLowerCase() || '';
  const [filteredTracks, setFilteredTracks] = useState(mockTracks);
  const [filteredPlaylists, setFilteredPlaylists] = useState(mockPlaylists);
  const [filteredArtists, setFilteredArtists] = useState(mockArtists);

  useEffect(() => {
    if (!query) {
      setFilteredTracks(mockTracks);
      setFilteredPlaylists(mockPlaylists);
      setFilteredArtists(mockArtists);
      return;
    }

    setFilteredTracks(
      mockTracks.filter(
        (track) =>
          track.title.toLowerCase().includes(query) ||
          track.artist.toLowerCase().includes(query) ||
          track.album.toLowerCase().includes(query)
      )
    );

    setFilteredPlaylists(
      mockPlaylists.filter((playlist) =>
        playlist.name.toLowerCase().includes(query)
      )
    );

    setFilteredArtists(
      mockArtists.filter((artist) =>
        artist.name.toLowerCase().includes(query)
      )
    );
  }, [query]);

  return (
    <div className="space-y-12">
      {/* Search Results Header */}
      <div>
        <h1 className="text-4xl font-bold mb-2">
          {query ? `Results for "${query}"` : 'Search'}
        </h1>
        {!query && <p className="text-spotify-text-secondary">Use the search bar above to find songs, artists, and playlists</p>}
      </div>

      {/* Artists */}
      {filteredArtists.length > 0 && (
        <section>
          <h2 className="text-2xl font-bold mb-6">Artists</h2>
          <div className="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-6">
            {filteredArtists.map((artist) => (
              <div key={artist.id} className="bg-spotify-card rounded-lg p-4 hover:bg-spotify-hover transition-all text-center">
                <img
                  src={artist.image}
                  alt={artist.name}
                  className="w-full aspect-square object-cover rounded-lg mb-4"
                />
                <h3 className="font-semibold text-white truncate">{artist.name}</h3>
                <p className="text-xs text-spotify-text-secondary">Artist</p>
              </div>
            ))}
          </div>
        </section>
      )}

      {/* Playlists */}
      {filteredPlaylists.length > 0 && (
        <section>
          <h2 className="text-2xl font-bold mb-6">Playlists</h2>
          <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
            {filteredPlaylists.map((playlist) => (
              <PlaylistCard key={playlist.id} playlist={playlist} />
            ))}
          </div>
        </section>
      )}

      {/* Tracks */}
      {filteredTracks.length > 0 && (
        <section>
          <h2 className="text-2xl font-bold mb-6">Tracks</h2>
          <TrackList tracks={filteredTracks} />
        </section>
      )}

      {/* No Results */}
      {query && filteredTracks.length === 0 && filteredPlaylists.length === 0 && filteredArtists.length === 0 && (
        <div className="text-center py-12">
          <p className="text-spotify-text-secondary mb-2">No results found for "{query}"</p>
          <p className="text-sm text-spotify-text-secondary">Try searching for different keywords</p>
        </div>
      )}
    </div>
  );
}
'use client';

import { useState } from 'react';
import PlaylistCard from '@/components/PlaylistCard';
import useMusicStore from '@/store/musicStore';
import TrackList from '@/components/TrackList';
import { Trash2 } from 'lucide-react';

export default function LibraryPage() {
  const { playlists, deletePlaylist, likedTracks } = useMusicStore();
  const [activeTab, setActiveTab] = useState<'playlists' | 'liked'>('playlists');

  return (
    <div className="space-y-8">
      {/* Header */}
      <div>
        <h1 className="text-4xl font-bold mb-2">Your Library</h1>
        <p className="text-spotify-text-secondary">Your saved playlists and liked songs</p>
      </div>

      {/* Tabs */}
      <div className="flex gap-4 border-b border-spotify-hover">
        <button
          onClick={() => setActiveTab('playlists')}
          className={`px-4 py-3 font-semibold transition-colors ${
            activeTab === 'playlists'
              ? 'border-b-2 border-spotify-green text-spotify-green'
              : 'text-spotify-text-secondary hover:text-spotify-text'
          }`}
        >
          Playlists ({playlists.length})
        </button>
        <button
          onClick={() => setActiveTab('liked')}
          className={`px-4 py-3 font-semibold transition-colors ${
            activeTab === 'liked'
              ? 'border-b-2 border-spotify-green text-spotify-green'
              : 'text-spotify-text-secondary hover:text-spotify-text'
          }`}
        >
          Liked Songs ({likedTracks.length})
        </button>
      </div>

      {/* Playlists Tab */}
      {activeTab === 'playlists' && (
        <div>
          {playlists.length === 0 ? (
            <div className="text-center py-12">
              <p className="text-spotify-text-secondary mb-2">No playlists yet</p>
              <p className="text-sm text-spotify-text-secondary">Create a playlist to get started</p>
            </div>
          ) : (
            <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
              {playlists.map((playlist) => (
                <div key={playlist.id} className="relative group">
                  <PlaylistCard playlist={playlist} />
                  <button
                    onClick={() => deletePlaylist(playlist.id)}
                    className="absolute top-2 right-2 p-2 bg-red-600 rounded-full opacity-0 group-hover:opacity-100 transition-opacity hover:bg-red-700"
                    title="Delete playlist"
                  >
                    <Trash2 size={16} className="text-white" />
                  </button>
                </div>
              ))}
            </div>
          )}
        </div>
      )}

      {/* Liked Songs Tab */}
      {activeTab === 'liked' && (
        <div>
          {likedTracks.length === 0 ? (
            <div className="text-center py-12">
              <p className="text-spotify-text-secondary mb-2">No liked songs yet</p>
              <p className="text-sm text-spotify-text-secondary">Like songs to add them to this list</p>
            </div>
          ) : (
            <TrackList tracks={likedTracks} />
          )}
        </div>
      )}
    </div>
  );
}
'use client';

import { useParams } from 'next/navigation';
import useMusicStore from '@/store/musicStore';
import TrackList from '@/components/TrackList';
import { Play } from 'lucide-react';
import Image from 'next/image';

export default function PlaylistPage() {
  const params = useParams();
  const playlistId = params.id as string;
  const { playlists, playTrack } = useMusicStore();

  const playlist = playlists.find((p) => p.id === playlistId);

  if (!playlist) {
    return (
      <div className="text-center py-12">
        <p className="text-spotify-text-secondary">Playlist not found</p>
      </div>
    );
  }

  return (
    <div className="space-y-8">
      {/* Playlist Header */}
      <div className="flex gap-6 items-end">
        <div className="w-40 h-40 flex-shrink-0 rounded overflow-hidden shadow-2xl">
          <Image
            src={playlist.coverUrl}
            alt={playlist.name}
            width={160}
            height={160}
            className="w-full h-full object-cover"
          />
        </div>
        <div>
          <p className="text-sm font-semibold text-spotify-text-secondary mb-2">PLAYLIST</p>
          <h1 className="text-5xl font-bold mb-4">{playlist.name}</h1>
          <p className="text-spotify-text-secondary mb-4">{playlist.description}</p>
          <div className="flex gap-4 items-center">
            {playlist.tracks.length > 0 && (
              <>
                <button
                  onClick={() => playTrack(playlist.tracks[0])}
                  className="flex items-center gap-2 px-8 py-3 bg-spotify-green text-black font-bold rounded-full hover:scale-105 transition-transform"
                >
                  <Play size={20} fill="black" />
                  Play
                </button>
                <p className="text-sm text-spotify-text-secondary">{playlist.tracks.length} songs</p>
              </>
            )}
          </div>
        </div>
      </div>

      {/* Tracks */}
      {playlist.tracks.length > 0 ? (
        <div>
          <h2 className="text-2xl font-bold mb-6">Tracks</h2>
          <TrackList tracks={playlist.tracks} showPlaylistOptions={true} playlistId={playlistId} />
        </div>
      ) : (
        <div className="text-center py-12">
          <p className="text-spotify-text-secondary">This playlist is empty</p>
        </div>
      )}
    </div>
  );
}
'use client';

import useMusicStore from '@/store/musicStore';
import TrackList from '@/components/TrackList';
import { Heart } from 'lucide-react';

export default function LikedPage() {
  const { likedTracks } = useMusicStore();

  return (
    <div className="space-y-8">
      {/* Header */}
      <div className="flex gap-6 items-end">
        <div className="w-40 h-40 flex-shrink-0 rounded bg-gradient-to-br from-spotify-green to-blue-600 flex items-center justify-center shadow-2xl">
          <Heart size={80} className="text-white" fill="white" />
        </div>
        <div>
          <p className="text-sm font-semibold text-spotify-text-secondary mb-2">PLAYLIST</p>
          <h1 className="text-5xl font-bold">Liked Songs</h1>
          <p className="text-spotify-text-secondary mt-4">{likedTracks.length} songs</p>
        </div>
      </div>

      {/* Tracks */}
      {likedTracks.length > 0 ? (
        <div>
          <TrackList tracks={likedTracks} />
        </div>
      ) : (
        <div className="text-center py-12">
          <p className="text-spotify-text-secondary">You haven't liked any songs yet</p>
        </div>
      )}
    </div>
  );
}
'use client';

import useMusicStore from '@/store/musicStore';
import TrackList from '@/components/TrackList';
import { Heart } from 'lucide-react';

export default function LikedPage() {
  const { likedTracks } = useMusicStore();

  return (
    <div className="space-y-8">
      {/* Header */}
      <div className="flex gap-6 items-end">
        <div className="w-40 h-40 flex-shrink-0 rounded bg-gradient-to-br from-spotify-green to-blue-600 flex items-center justify-center shadow-2xl">
          <Heart size={80} className="text-white" fill="white" />
        </div>
        <div>
          <p className="text-sm font-semibold text-spotify-text-secondary mb-2">PLAYLIST</p>
          <h1 className="text-5xl font-bold">Liked Songs</h1>
          <p className="text-spotify-text-secondary mt-4">{likedTracks.length} songs</p>
        </div>
      </div>

      {/* Tracks */}
      {likedTracks.length > 0 ? (
        <div>
          <TrackList tracks={likedTracks} />
        </div>
      ) : (
        <div className="text-center py-12">
          <p className="text-spotify-text-secondary">You haven't liked any songs yet</p>
        </div>
      )}
    </div>
  );
}

